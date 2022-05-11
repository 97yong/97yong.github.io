---
title:  "[Lecture 1] Pytorch CNN으로 숫자이미지 분류"
excerpt: "숫자 이미지 분류"

categories:
  - DL Code
tags:
  - [python, coding, deeplearning]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
use_math: true

date: 2022-04-29 # 글을 처음 작성한 날짜
last_modified_at: 2022-05-11 # 이 글을 수정한 날짜.
---

## 0. CNN(Convolutional Neural Network)

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/166412538-84937f68-adb9-440d-b13f-e30e87618068.png" width="600" height="auto">
</p>

 - CNN은 DNN(Deep Neural Network)보다 발전된 기술입니다. 이미지로부터 Filter의 개수와 같은 하이퍼파라미터를 조정하면서 특징추출을 자동화해주는 신경망의 일종입니다.
 - 그림을 보면 DNN은 뒤쪽 레이어처럼 노드하나 하나가 연결된 형태라면, CNN은 Filter를 통해 여러 부분을 한번에 포착해서 작동하기 때문에 이미지상에서 translation이나 Rotation같은 특성에 유리합니다.

## 1. CNN Code

### 1.1. 라이브러리 불러오기

```py
import time
import os
import copy

import numpy as np

import torch
import torch.nn as nn
import torch.nn.functional as F
import torch.optim as optim

import torchvision
from torchvision import datasets, models, transforms
from torch.utils.data import Dataset, DataLoader

import matplotlib.pyplot as plt
```

 - 숫자 이미지를 분류하기 위한 라이브러리를 불러옵니다.
 - torchvision은 숫자이미지 데이터를 불러오기 위한 라이브러리입니다.
 - matplotlib는 그래프나 그림을 나타내기 위해 사용하는 라이브러리입니다.

### 1.2. gpu 모델 확인

```py
device = "cuda" if torch.cuda.is_available() else "cpu"
device
```
 - 여기에서는 cuda라고 뜨면 gpu가 활성화 되어 있는 것입니다.
 > Q. cpu라고 뜹니다.
 >> A. Lecture 0를 확인해주세요!

### 1.3 데이터셋 준비하기

```py
mnist_train = dsets.MNIST(root='MNIST_data/', # 파일을 다운로드 경로
                          train=True, # True는 훈련 데이터를 의미
                          transform=transforms.ToTensor(), # 파이토치는 텐서로 연산이 되므로 텐서로 변환함
                          download=True)

mnist_test = dsets.MNIST(root='MNIST_data/', # 다운로드 경로 지정
                         train=False, # False는 테스트 데이터를 의미
                         transform=transforms.ToTensor(),
                         download=True)
```

 - 위의 코드는 데이터셋을 다운로드하는 코드입니다.
 - 현재 코드내에 MNIST_data라는 폴더가 생기면서 이미지 파일이 생성됩니다.

### 1.5 CNN 모델 만들기

```py
class Model(nn.Module):
    def __init__(self):
        super(Model, self).__init__()
        self.model = nn.Sequential(nn.Conv1d(1, 64, kernel_size=3),
                                                     nn.MaxPool1d(2), 
                                                     nn.ReLU(),
                                                     nn.Conv1d(64, 128, kernel_size=3),
                                                     nn.MaxPool1d(2),
                                                     nn.ReLU(),
                                                     nn.Flatten(),
                                                     nn.Linear(3200,256),
                                                     nn.ReLU(),
                                                     nn.Linear(256, 10)
                                                    )
    def forward(self, x):
        x = self.model(x)
        return x
        
model = Model().to(device)
```

### 1.6 파라미터 정의

```py
batch_size = 512
learning_rate = 0.001
num_epochs = 30
loss_func = nn.CrossEntropyLoss()
optimizer = optim.Adam( model.parameters(), lr=learning_rate )
```

### 1.7 데이터로더로 데이터 보내기

```py
train_dl = DataLoader(mnist_train, batch_size=batch_size, shuffle=True)
test_dl = DataLoader(mnist_test, batch_size=batch_size, shuffle=False)
```

### 1.8 train/test 함수
```py
def train(epoch, num_epochs, model, optimizer):
    model.train()

    for batch, target in train_dl:
        batch, target = batch.to(device), target.to(device)

        pred = model( batch )

        # calculate the loss
        loss = loss_func( pred, target )
        
        # 이전 그레디언트 삭제
        optimizer.zero_grad()
        # 현재 그레디언트 계산
        loss.backward()
        # 가중치 업데이트
        optimizer.step()

    return loss
    
def test(model):
    model.eval()

    correct = 0
    
    # 그레디언트 계산 안하도록
    with torch.no_grad():
        for batch, target in test_dl:
            batch, target = batch.to(device), target.to(device)

            pred = model( batch )

            # 라벨이 무엇인지 계산
            output = torch.argmax(pred, 1)

            correct += (output == target).sum().item()

    # 정확도 계산
    acc = 100 * float(correct) / len(test_dataset)   
    
    return acc
```

### 1.10 훈련하기

```py
for epoch in range(num_epochs):

    # train
    train_loss = train(epoch+1, num_epochs, model, optimizer)
    # test
    acc = test(model)

    print( 'Epoch: {} --- Train Loss: {:.4f} Test Acc: {:.2f}%'.format( epoch+1, train_loss , acc ) )


print('Training completed')
```

### 1.11 결과 확인하기

```py
classes = mnist_train.classes

def convert_format(image):
    image = image / 2 + 0.5
    image = image.numpy()
    image = image.clip(0,1)

    return image.transpose(1,2,0)

def visualize_model(model, num_images=6):
    model.eval()
    images_so_far = 0
    fig = plt.figure(figsize=(12,12))

    with torch.no_grad():
        for i, (images, labels) in enumerate(test_dl):
            images = images.to(device)
            labels = labels.to(device)

            outputs = model(images)
            _, preds = torch.max(outputs, 1)

            for j in range(images.size()[0]):
                images_so_far += 1
                ax = plt.subplot(1, num_images, images_so_far)
                ax.axis('off')
                ax.set_title('pred: {}'.format(classes[preds[j]]))
                ax.imshow( convert_format(images.cpu().data[j]) )

                if images_so_far == num_images:
                    return

visualize_model(model)      
```

- 잘 훈련되었다면 다음과 같은 그림이 나오게 될 것입니다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/167844487-e8bdacdf-7841-4905-802a-aa78ef92b7f7.png" width="700" height="auto">
</p>


  > 구체적인 설명은 추후에 작성하겠습니다. 질문이 있다면 댓글이나 이메일로 문의해주세요!

## Reference
LeCun, Yann, et al. "Gradient-based learning applied to document recognition." Proceedings of the IEEE 86.11 (1998): 2278-2324.
Ayyadevara, V. Kishore, and Yeshwanth Reddy. Modern Computer Vision with PyTorch: Explore deep learning concepts and implement over 50 real-world image applications. Packt Publishing Ltd, 2020.
