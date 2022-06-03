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

## 2. Model Agnoistic Meta-Learning

- Model Agnoistic(모델과 상관없이) 훈련될 수 있는 Meta-Learning

### 2.1. Meta-Learning Problem Set-Up

- 목표: 작은 데이터와 적은 iteration으로 새로운 task에 대해 모델을 적응시키는 것

- Generalized Model의 θ를 최적화 하는 방향으로 Gradient Descent를 진행

### 2.2. A Model-Agnostic Meta-Learning Algorithm

- Task의 변화에 민감한 모델의 parameter를 훈련하는 것이 목표

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/171654934-afce9e46-5dea-4ffe-92c3-9b65a6f8471c.png" width="600" height="auto">
</p>

- 제안하는 방법은 위의 그림에서, 새로운 task에 대해 여러 gradient를 계산해서 업데이트를 하게 된다.

- 구체적으로 \\(θ\\)는 1,2,3 에 대해서 제일 좋은 방향은 아니지만 저 방향으로 \\(θ\\)가 학습된다면 이후 가장 빠르게 Adaptation을 할 수 있게 된다.
  > \\(θ\\)는 이후 새로운 Task \\(T_i\\) 에 맞는 \\(θ^*\\)을 찾아간다. (Fast Adaptation)

- \\(\min(θ)\sum(T_i~p(T)) L_T_i(f_θ\prime_i) = \sum(T_i~p(T)) L_T_i(f_θ_i) f_θ-\alpha \bigtriangledown_θ L_T_i (f_θ)  \\)
