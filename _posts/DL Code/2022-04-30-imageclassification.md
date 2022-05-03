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
last_modified_at: 2022-04-29 # 이 글을 수정한 날짜.
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



- 아직 작성중입니다.



## Reference
LeCun, Yann, et al. "Gradient-based learning applied to document recognition." Proceedings of the IEEE 86.11 (1998): 2278-2324.
