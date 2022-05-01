---
title:  "[Lecture 0] Pytorch 설치방법 (Cuda 설정까지)"
excerpt: "파이썬 설치"

categories:
  - DL Code
tags:
  - [python, coding, deeplearning]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
 
date: 2022-04-29 # 글을 처음 작성한 날짜
last_modified_at: 2022-04-29 # 이 글을 수정한 날짜.
---

## 0. 아나콘다 설치

 - Anaconda 들어가기 (<https://www.anaconda.com/products/distribution>)

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/165921520-fcac1440-7863-40ea-afa5-49a9cf582a81.png" width="600" height="auto">
</p>

 - <https://97yong.github.io/python/install_python/>
 - 구체적인 Anaconda 다운로드는 블로그의 위 포스트를 참고해주세요!
 - 위의 설치과정을 다 따라하셨다면 1.4로 바로 이동해주세요!


## 1. 파이토치 설치

 - 포스트는 Window10 기준으로 작성되었습니다.
 - 파이썬 버전은 3.7 입니다.
 - 파이토치 버전은 1.10.2 입니다.
 - <u>CuDNN등 여러 스트레스를 받지 않고 한번에 설치가 가능합니다.</u>
 
### 1.1. 파이썬 설치
```py
conda create -n 이름 python=3.7
```
 - 명령프롬프트에서 가상환경에 파이썬 3.7버전을 설치해줍니다.

### 1.2. 가상환경 활성화
```py
conda activate 이름
```
 - 가상환경을 활성화합니다.

### 1.3. ipykernel 설치
```py
conda install ipykernel jupyter
```
 - ipykernel 라이브러리 사용을 위해 ipykernel을 설치합니다.

### 1.4. display 설정
```py
python -m ipykernel install --user --name 이름 --display-name “이름”
```
 - 환경 이름을 보여주기 위해 display 이름을 설정합니다
 - 가상환경 이름과 똑같은 이름으로 설정해주시면 됩니다.

### 1.5. pytorch 설치

- 자신의 그래픽카드가 GTX의 종류가 아닌 경우 2.1을 먼저 읽어주세요.

```py
conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch
```

- 파이토치와 cudatoolkit(GPU연산을 가능하게 해주는 도구)를 설치해줍니다.

 > Q. 왜 cpu가 아닌 cuda를 사용하나요?
 >> A. 딥러닝은 간단한 수학연산을 수백만번 연산하게 됩니다. GPU는 이러한 간단한 연산을 병렬적으로 처리할 수 있고, 이는 딥러닝 계산속도를 엄청나게 빠르게하기 때문에 GPU를 사용합니다. 실제로 cuda를 설정하지 않고 코드를 돌려볼 경우 크게는 10배이상의 속도차이가 나는 것을 확인할 수 있습니다.

### 1.6. 파이토치에 유용한 라이브러리 설치

```py
pip install torchsummary
```

```py
pip install torch_snippets
```

```py
pip install jupyterlab
```
 - 저는 주피터랩 사용예정이라 주피터랩을 설치했습니다.

## 2. 파이토치 gpu 설정 확인

 - 주피터노트북이나 주피터랩에 들어갑니다.

```py
device = "cuda" if torch.cuda.is_available() else "cpu"
print(device)
```
 - 결과가 cuda 라고 떴으면 성공입니다.

 > Q. 결과가 cpu라고 뜹니다.
 >> A. 아래의 2.1을 확인해주세요.

### 2.1. gpu가속이 안되는 경우

 - 저는 GTX 1080Ti 버전에서 설치를 했습니다.
 - 간혹 GPU에 따라 버전이 맞지 않는 경우가 있습니다.
 - RTX A6000 그래픽 카드에서는 10.2를 11.3으로 변경해주어야 했습니다.
 
 - <https://www.nvidia.co.kr/Download/index.aspx?lang=kr>
 - 자신의 환경에 맞는 gpu를 설치합니다.
 - Window키+R -> cmd 를 입력합니다. (주의: anaconda prompt와 다른 프롬프트입니다.)
 - nvcc -V 를 입력하고 release 뒤에 오는 버전이 Cuda 버전입니다.
 
 - <https://pytorch.org/get-started/previous-versions/>
 - 위의 사이트에서 자신에게 맞는 Cuda 버전을 찾아준 후에 <u>1.5</u>의 코드를 바꿔줍니다. 
