---
title:  "[Lecture 0] Python 설치"
excerpt: "파이썬 설치"

categories:
  - python
tags:
  - [python, coding]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
 
date: 2022-04-29 # 글을 처음 작성한 날짜
last_modified_at: 2022-04-29 # 이 글을 수정한 날짜.
---

## 1. 아나콘다 설치

 - 이 글은 Window10 버전을 기준으로 작성되었습니다.
 - 
### 1.1. 아나콘다 사이트 들어가기

 - Anaconda 들어가기 (<https://www.anaconda.com/products/distribution>)

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/165921520-fcac1440-7863-40ea-afa5-49a9cf582a81.png" width="600" height="auto">
</p>

### 1.2. 아나콘다 다운로드

 - Download를 눌러주세요!
  > Q. 버전은 어떤 것을 다운 받나요? 
  >> A.가상환경을 만들 것이기 때문에 버전이 상관이 없습니다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/165922570-5d17c826-bec7-4cd1-8a08-b8bf1981b358.png" width="400" height="auto">
</p>

### 1.3. 프롬프트 열기

 - 설치가 완료되면 윈도우 검색탭에 Anaconda Prompt (Anaconda3)이라는 파일을 찾을 수 있습니다다.
 - Click!

## 2. 가상환경 설치

### 2.1. 가상환경 설치

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/165923260-bd73db7a-e8dd-465b-9e34-2baf59a9ad61.png" width="400" height="auto">
</p>

 - conda create -n "원하는 가상환경 이름" python=3.7 을 입력한다.
 - 저는 주로 3.7버전을 사용하기 때문에 3.7이라고 입력을 하였고, 원하시는 버전에 따라 입력하시면 됩니다. (나중에 딥러닝 버전과 맞추기 위함입니다.)
 - y를 누르면 설치가 완료됩니다.

### 2.2 가상환경 활성화

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/165923506-d4ef0c30-cddf-40cc-903f-f9266e22210a.png" width="400" height="auto">
</p>

- 가상환경에 접근하는 코드입니다.
- 이를 통해 환경이 base에서 사용자가 지정한 가상환경에 접근하게 됩니다.
 > Q. 왜 가상환경을 만드나요?
 >> A. 가상환경은 자신이 원하는 버전을 다운받아 사용할 수 있고, 나중에 다양한 개발을 할 때 손쉽게 사용할 수 있습니다. 실제로 저는 파이토치는 yong이라는 가상환경에서 개발을 하고 TensorFlow는 yongtf라는 환경에서 개발을 합니다. 또한, 코스웍(학교수업)을 들을 때는 class라는 가상환경을 만들어 개발을 하고 있습니다.

### 2.3. ipykernel 설치

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/165924144-c7fbc5ac-64a0-450b-aead-67d92084d327.png" width="400" height="auto">
</p>

- 위 그림처럼 (yong)을 보시면 yong에 잘 접근이 된 것을 볼 수 있고 ipykernel 관련 라이브러리 사용을 위해 ipykernel을 설치해줍니다.
- 저는 이미 설치되어 있어서 다음으로 넘어가겠습니다.

### 2.4. jupyter notebook 설치

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/165924605-f06e1cb1-d283-4127-8042-75a3d1bcbf06.png" width="400" height="auto">
</p>

- <u>주피터 노트북</u>을 설치합니다.

### 2.5. 주피터 노트북 실행

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/165924605-f06e1cb1-d283-4127-8042-75a3d1bcbf06.png" width="400" height="auto">
</p>

- 주피터 노트북을 실행합니다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/165925033-7447eb29-0772-48bc-9c15-f1e1adb29edc.png" width="400" height="auto">
</p>

- 저는 class에 jupyter notebook이 설치되어 있어서 가상환경을 바꾸겠습니다. (제 환경에는 jupyter lab이 깔려 있습니다.)
 > Q. jupyter notebook과 jupyter lab의 차이는 무엇인가요?
 >> A. 비슷하지만 처음할때는 jupyter notebook이 편하고, 이후 연구를 위해서는 파일을 빠르게 이동할 수 있는 jupyter lab이 편합니다.

