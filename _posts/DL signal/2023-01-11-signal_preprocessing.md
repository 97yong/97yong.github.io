---
title:  "[Lecture 0] 1차원 신호처리 (딥러닝)"
excerpt: "딥러닝을 위한 1차원 신호처리"

categories:
  - DL Signal
tags:
  - [python, coding, deeplearning, signal]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
use_math: true

date: 2023-01-11 # 글을 처음 작성한 날짜
last_modified_at: 2023-01-11 # 이 글을 수정한 날짜.
---

## 0. 1차원 신호

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/211735827-5d1a055d-27c2-4261-a6a4-3e740ffa2f66.png" width="600" height="auto">
</p>

 - 안녕하세요! 방학한 기념으로 시간이 날 때마다 1차원 신호에 대해 딥러닝을 할 수 있도록 차근차근 설명을 시작해보려고 합니다.
 - 저는 위의 그림과 같은 1차원 진동신호를 연구하고 있는데요. 신호마다 데이터 처리방법이나 딥러닝 모델 구조 등등 다를 수도 있다는 점 참고해주시면 감사하겠습니다.

 > Q. 1차원 신호란?
 >> A. 쉽게 말해 차원이 한개인 신호입니다. 예를 들어 우리가 컴퓨터 화면으로 쉽게 볼 수 있는 사진은 2차원 이미지라고 하고, 우리가 현실세계에서 보는 물체들은 3차원 물체라고 합니다.
 
 - 1차원 신호는 단순하게 표현될 수 있지만, 이미지와 달리 물리적인 요소가 굉장히 많이 포함되어 있어 전기전자공학, 기계공학에서 주로 다루게 됩니다.
 
 ## 1. 데이터 불러오기
 
  - 본격적으로 데이터를 불러오는 과정을 포스팅하겠습니다.
  - 저는 아래의 CWRU bearing data를 사용하였습니다. 이번 포스트에서는 0.007" 0HP, OR007@6_0 데이터를 사용하겠습니다.
  
  > 베어링 고장은 대표적으로 내륜고장, 볼고장, 외륜고장이 존재합니다. 저는 고장특성이 잘 드러나는 외륜고장으로 사용하였습니다. ( 추가적으로 궁금하신 분은 댓글 부탁드립니다 :) )
  
  Data Link: <a href="https://engineering.case.edu/bearingdatacenter/12k-drive-end-bearing-fault-data">1 dimensional signal - CWRU DATASET</a>
  
  <p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/211737336-b3b3f501-00ca-4d90-ab73-6028a3da0a37.png" width="600" height="auto">
</p>
  
  - 데이터를 다운받으시고 다음과 같이 아무 폴더에 data 폴더를 만들고 data폴더에 데이터를 넣어주세요. (파이썬을 잘 다루시는 분들이라면 상관없지만, 처음부터 따라오시는 분들을 위해 추천합니다.)
  - jupyter lab이나 jupyter notebook을 켜서 코딩을 시작하도록 하겠습니다. (파이썬 설치나, pytorch 설치가 안되신 분들은 블로그에 설치순서대로 다운해주시면 되겠습니다.)

## 1.1 라이브러리 불러오기

```py
import sys
import os
import numpy
import pandas as pd
import matplotlib.pyplot as plt
```

 - 우선 사용할 파이썬 라이브러리를 불러옵니다.
 
 ## 1.2 Matlab 파일 처리하기

```py
data_path = os.path.join(os.getcwd(), 'data')

from scipy.io import loadmat

signal = loadmat(data_path + '/130.mat')

print(signal)
```

 - data_path를 지정해줍니다. getcwd()를 통해 현재 위치를 불러올 수 있고, data의 경로를 지정해줄 수 있습니다.
 > Q. 이러한 방법이 편한가요?
 >> A. 개인의 취향이지만, 저는 다음과 같이 경로를 관리합니다. 왜냐하면 컴퓨터를 옮기거나 다른 컴퓨터에서 작업할 때, 폴더만 옮겨주게 되면 어느 곳에서도 작동하기 때문에 이러한 방법을 추천드립니다.
 
 - CWRU data는 matlab파일이어서 matlab 파일을 처리해주는 과정을 거쳐야합니다.
 - scipy 라이브러리에 loadmat을 사용해 불러오도록 하겠습니다.
 
   <p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/211738611-eb6fd3e2-fc6d-4e91-a421-a440d5ff5294.png" width="600" height="auto">
</p>

 - 다음과 같이 output이 나오는 것을 알 수 있습니다. Matlab을 사용하지 않으신 분들은 새로워 보일 수 있지만, dictionary 형태로 되어 있어 쉽게 데이터를 불러올 수 있습니다.
 - 참고로 DE, FE등등은 Drive End, Fan End의 줄임말으로 센서의 위치를 의미합니다.
 - 저희는 Drive End의 파일을 불러오도록 하겠습니다.
 
 ## 1.3 데이터 Plot
 
 ```py
plt.plot(signal['X130_DE_time'][:2000], 'black')
```

 - key를 'X130_DE_time'으로 입력해주고 데이터의 길이가 길기 때문에 2000까지만 plot하게 되면 다음과 같은 신호가 출력되게 됩니다!

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/211735827-5d1a055d-27c2-4261-a6a4-3e740ffa2f66.png" width="600" height="auto">
</p>
