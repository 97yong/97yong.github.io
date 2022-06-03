---
title:  "[논문리뷰] Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks"
excerpt: "International conference on machine learning (2017)"

categories:
  - DL Paper
tags:
  - [paper, deeplearning]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
use_math: true

date: 2022-06-02 # 글을 처음 작성한 날짜
last_modified_at: 2022-06-02 # 이 글을 수정한 날짜.
---

## 0. Information

- 2022-06-02 기준 6131회 인용
<br>

## 1. Introduction

- Transfer learning VS Meta learning
  > Transfer learning: 미리 학습된 모델에 적은 dataset에 대해 Fine Tuning하는 과정

  > Meta learning: Learning to learn이라는 느낌으로 전이학습보다 빠르게 adaptation하는 알고리즘

- Meta-learning 알고리즘을 제안

- 메타러닝에서 모델훈련의 목표는 새로운 작은 양의 데이터로 새로운 task를 빠르게 배우는 것이다. 그리고 나서 많은 양의 task로 부터 훈련된다.
  > 이를 어떻게 해결할까?
  >> 모델의 성능을 최대한으로 이끌어 줄 수 있도록 모델의 initial parameter를 훈련시키는 것이다!

- 제안하는 방법은 새로운 Task에 관해 손실함수의 민감도를 최대화시킨다.

- 새로운 Task의 데이터가 들어오면 여러 Task에 동시에 최적화된 Model의 Parameter를 찾는다.

- 이 모델은 쉽게 다른 여러 neural network 모델과 결합될 수 있다.
<br>

## 2. Model Agnoistic Meta-Learning

- Model Agnoistic(모델과 상관없이) 훈련될 수 있는 Meta-Learning
<br>

### 2.1. Meta-Learning Problem Set-Up

- 목표: 작은 데이터와 적은 iteration으로 새로운 task에 대해 모델을 적응시키는 것

- Generalized Model의 θ를 최적화 하는 방향으로 Gradient Descent를 진행
<br>

### 2.2. A Model-Agnostic Meta-Learning Algorithm

- Task의 변화에 민감한 모델의 parameter를 훈련하는 것이 목표

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/171654934-afce9e46-5dea-4ffe-92c3-9b65a6f8471c.png" width="600" height="auto">
</p>

- 제안하는 방법은 위의 그림에서, 새로운 task에 대해 여러 gradient를 계산해서 업데이트를 하게 된다

- 구체적으로 \\(θ\\)는 1,2,3 에 대해서 제일 좋은 방향은 아니지만 저 방향으로 \\(θ\\)가 학습된다면 이후 가장 빠르게 Adaptation을 할 수 있게 된다.
  > \\(θ\\)는 이후 새로운 Task \\(T_i\\) 에 맞는 \\(θ^*\\)을 찾아간다. (Fast Adaptation)

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/171774971-d3017598-3cfb-40f7-bd01-470e8566e1fa.png" width="400" height="auto">
</p>

- \\(P(T)\\): 전체 Task, \\(T_i\\): 새로운 Task

- 모델은 \\(θ\\)로 initialize 되어있고, Task에 맞는 loss function에 대해 SGD를 진행

- 새로운 Task들에 대해 각각 \\(θ_i\prime\\)을 구하고, 각각의 \\(θ_i\prime\\)에 대한 Loss들의 합을 SGD해서 \\(θ\\)를 업데이트

- 계산과정에서 Hessian vector의 곱으로 계산되는데, 저자는 first-order approximation을 사용한다. (이는 5.2에서 다시 이야기한다.)

  > 결론은 first-order approximation을 사용해도 정확도의 차이가 없다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/171787444-b68557d1-a8ec-4688-9bcf-2a5af044c632.png" width="400" height="auto">
</p>

- 다시 그림을 그려 정리해보자면, 우리는 모델의 \\(θ\\)를 업데이트하는 것이 주목표이다.

- 이를 위해 Task에 대한 각각의 gradient를 구해서 Task 각각에 대한 \\(θ_i\prime\\)를 찾는다. (여기서 한번에 찾을 수도 있고, 여러번에 걸쳐서 찾을 수도 있다.)

- \\(θ_i\prime\\)을 모델에 넣어 자신의 Task에 해당하는 Loss를 구해 그에 대한 합을 최종 Loss로 생각한다.

- 이에 대한 Loss를 업데이트를 반복해서 \\(θ\\)를 찾는다.

<br>
## 3. Species of MAML

- 지도 학습과 강화학습에 대해 메타러닝 알고리즘에 대해 discuss한다.

<br>
### 3.1. Supervised Regression and Classification

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/171775050-674a2ea5-7514-4d22-949b-ac596ee53044.png" width="400" height="auto">
</p>

- 대표적으로 Fewshot learning이 있다.
  > Fewshot learning: 유사성을 학습하는 알고리즘. 이에 적은 데이터를 효율적으로 학습

- 분류문제에서 Fewshot learning의 목표: 이전에 많은 다른 종류의 class를 본 모델을 사용하여 하나 또는 몇개를 본 후에 이미지를 분류하는 것 

<br>
### 3.2. Reinforecement Learning

- 생략 ( 본 포스터에서는 분류에 해당하는 문제만 다룸 )

<br>
## 4. Related Work

- Meta learning과 Few shot learning이 풀고자 하는 문제, 저자의 접근 방법등에 대한 전반적인 내용을 담고 있음.

<br>
## 5. Experimental Evaluation

- ( 본 포스터에서는 분류 문제에 대해서만 다룸 )
 
<br>
### 5.2. Classification

- Omniglot 과 MiniImagenet 데이터셋에 대해 실험

- 모두 제안하는 방법이 우수한 결과를 보임.

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/171790231-9bb00f8d-1510-4964-93c8-ca039d1fd476.png" width="400" height="auto">
</p>

- 위의 그림에서 제안하는 방법인 MAML을 이용한 알고리즘이 최종 목표에 잘 도달하는 것을 확인할 수 있다.
