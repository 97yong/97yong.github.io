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

- Meta-learning 알고리즘을 제안
- 메타러닝에서 모델훈련의 목표는 새로운 작은 양의 데이터로 새로운 task를 빠르게 배우는 것이다. 그리고 나서 거대한 양의 데이터를 학습시킬 수 있는 모델이 훈련된다.
  > 이를 어떻게 해결할까?
  >> 모델의 성능을 최대한으로 이끌어 줄 수 있도록 모델의 initial parameter를 훈련시키는 것이다!

- 쉽게 다른 여러 neural network 모델과 결합될 수 있다.
- 제안하는 방법은 새로운 Task에 관해 손실함수의 민감도를 최대화시킨다.

## 2. Model Agnoistic Meta-Learning

### 2.1. Meta-Learning Problem Set-Up

- 목표: 작은 데이터와 적은 iteration으로 새로운 task에 대해 모델을 적응시키는 것
- 메타러닝 시나리오에 있어서 K sample을 일으키는 q의 변화로 부터 모델을 향상시킬 수 있음
- 

### 2.2. A Model-Agnostic Meta-Learning Algorithm

- Task의 변화에 민감한 모델의 parameter를 훈련하는 것이 목표

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/171654934-afce9e46-5dea-4ffe-92c3-9b65a6f8471c.png" width="600" height="auto">
</p>

- 제안하는 방법은 위의 그림에서, 새로운 task에 대해 여러 gradient를 계산해서 업데이트를 하게 된다.
