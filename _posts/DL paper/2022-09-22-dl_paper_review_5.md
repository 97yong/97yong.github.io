---
title:  "[논문리뷰] Domain Generalization via Entropy Regularization"
excerpt: "NeurIPS (2020)"

categories:
  - DL Paper
tags:
  - [paper, deeplearning]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
use_math: true

date: 2022-09-22 # 글을 처음 작성한 날짜
last_modified_at: 2022-09-22 # 이 글을 수정한 날짜.
---

## Summary

- 기존의 Domain Adversarial Network들은 Invariant한 Marginal distribution을 보증해왔다.

- 하지만, Domain generalization에서 Conditional distribution이 중요한데, 본 논문에서는 Entropy Regularization을 사용해 목적을 이루어내었다.

<br>

## 0. Information

- 2022-09-22 기준 78회 인용

- Computer Vision 분야의 유명 학회

<br>

## 1. Introduction

- Training data를 통해 학습된 모델은 다른 분포의 데이터에 대해 잘 일반화되지 않는다.

  > 이미지 사진에 대해 학습된 모델을 가지고 그림사진을 예측하려하면 잘 예측하지 못한다.

- 이를 해결하기 위해 Domain Adaptation이 만들어졌고 이는 Source domain과 Target domain사이에 분포를 줄여주었다.

  > Source domain: 주어진 훈련데이터, Target domain: 레이블이 없는 데이터

- 하지만 위의 Domain adaptation 문제는 데이터셋마다 학습을 시켜야하고 time-consuming이 발생한다.

- Domain Generalization은 여러 다른 Source domain을 학습시켜 일반화된 모델을 만드는 것이다. (Unseen data도 예측가능하다.)

- 앞서 개발된 Domain Generalization에 대한 연구들을 소개

- 대부분의 존재하는 방법들은 Marginal distribution는 변하지만 Condtional distribution이 안정적이라고 가정한다. 하지만 실제 데이터들은 그렇지 못하다.

- 실제 데이터들은 X가 변함에 따라 Y의 분포가 변하게 되는데, 본 논문에서는 Entropy Regularization이라는 방법을 도입해 P(Y|F(X))를 직접적으로 학습시키도록 한다.

- 저자들은 Cross-Entropy loss보다 모든 소스 도메인에서 loss를 효과적으로 최소화할 수 있다고 말하고 있다.

<br>

## 2. Method

### 2.1 Problem Definition

- Domain Generalization문제에서 K개의 Source domain이 존재하고 L개의 Target domain이 존재한다. 목표는 Source domain으로 부터 모델을 학습시켜 Unseen(한번도 보지 못한) Target 데이터에도 일반적으로 잘 예측하도록 하는 것이다.

- K개의 도메인을 통해 학습을 하고 L개의 도메인을 통해 평가한다.

### 2.2 Domain Generalization Through Adversarial Learning



<!-- <p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/176616983-d0b0f506-e8f9-43c6-b92f-6fe75014b8db.png" width="600" height="auto">
</p> -->



### Referenece
- Zhao, Shanshan, et al. "Domain generalization via entropy regularization." Advances in Neural Information Processing Systems 33 (2020): 16096-16107.
