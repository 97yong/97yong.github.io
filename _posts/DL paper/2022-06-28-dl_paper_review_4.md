---
title:  "[논문리뷰] Adversarial domain-invariant generalization: A generic domain-regressive framework for bearing fault diagnosis under unseen conditions"
excerpt: "IEEE Transactions on Industrial Informatics (2021)"

categories:
  - DL Paper
tags:
  - [paper, deeplearning]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
use_math: true

date: 2022-06-28 # 글을 처음 작성한 날짜
last_modified_at: 2022-07-28 # 이 글을 수정한 날짜.
---

## Summary

- open source data를 제공하고 transfer learning방법에 대한 성능비교를 한다.
<br>

## 0. Information

- 2022-06-28 기준 11회 인용

- JCR IF 2020 기준 11.648 (Q1)

- 2021년에 출판된 최신 논문임.
<br>

## 1. Introduction

- 기계시스템의 중요한 부품 중에 하나인 베어링은 여러 다른 운영조건 하에 작동된다. 그래서 cross-domain fault diagnosis가 제안되었다.

- 하지만 기계시스템에 대해 source data와 target data의 분포가 서로 달랐고 이 discrepenacy는 domain shift를 유발했다.

- 연구자들은 MMD, CORAL, JMMD등 여러 연구를 통해 domain shift를 줄여왔다. 또한 도메인의 불변의 feature를 추출하기 위해 adversarial training과 앙상블 학습 등을 도입했다.

- 이러한 연구들은 target data에 대해 충분한 데이터가 없을 때 어려움을 겪는다. 그래서 Partial DA(target data는 source data label의 일부만 가지고 있음) 이나 few-shot learning들이 개발되어 왔다.

- 앞서 연구들에 두가지 문제점들이 있다.
  
  > 1. target 데이터가 없으면 어떻게 될 까?

  > 2. 기존의 transfer learning은 Source로부터 Target을 예측해, 하나의 도메인에만 overfit이 되었다.

- 따라서 여러 도메인에 대해 <u>Gerneric diagnosis knowledge</u>가 필요하다.

- 본 논문은 Domain generalization (DG) 문제를 해결하고자 한다.
<br>

### Main Contibution

1. 제안하는 알고리즘은 도메인 불변의 지식을 학습한다.

2. instance 간의 normalization과 spectral normalization은 도메인 특성간의 일반화를 만들었다. 또한 adaptive weight를 통해 성능을 향상시켰다.

3. 여러 실험을 통해 제안하는 방법을 평가했고 보지 않은 타겟 condition을 진단했다.
<br>

## 2. Preliminaries

### A. Domin Adaptation

- Domain Adaptation에서는 source가 label이 있고 target이 label이 없는 상황에서 문제를 해결하려고 한다.
<br>

### B. Domain Generalization

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/176616983-d0b0f506-e8f9-43c6-b92f-6fe75014b8db.png" width="600" height="auto">
</p>

- 그림처럼 Domain Generalization은 target 데이터를 이용하지 않고 source data 만으로 학습해 target data를 분류하는 것이다.

  > Domain Adaptation은 target data를 사용하지만 Domain Generealization은 그렇지 못해 더 어렵다. 하지만 여러 source domain을 사용하기 때문에 generalization을 할 수 있다는 강력한 능력을 가지고 있다.
<br>

### C. Generative Adversarial Network

- Generative Adversarial Network(GAN)은 real-world에 대한 data를 학습한다. 그래서 Latent space에서 real-world data space로 mapping하는 것을 학습한다.

- 최근 연구자들은 DA를 하기 위해 GRL(Gradient Reversal Layer)를 적용해 GAN과 비슷한 학습방법을 채택했다.

## 3. Proposed Method

### A. Generic Domain-Regressive Framework

- 각 샘플들은 FFT와 reshape을 통해 2D 이미지로 변환된다.

- domain classifier에 SN(Spectral Normalization)을 사용한다.

### B. Feature Normalization Strategy

- 



<br>

## Reference

- Chen, Liang, et al. "Adversarial domain-invariant generalization: A generic domain-regressive framework for bearing fault diagnosis under unseen conditions." IEEE Transactions on Industrial Informatics 18.3 (2021): 1790-1800.
