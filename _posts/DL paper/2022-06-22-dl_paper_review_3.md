---
title:  "[논문리뷰] Applications of unsupervised deep transfer learning to intelligent fault diagnosis: A survey and comparative study"
excerpt: "IEEE Transactions on Instrumentation and Measurement (2021)"

categories:
  - DL Paper
tags:
  - [paper, deeplearning]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
use_math: true

date: 2022-06-21 # 글을 처음 작성한 날짜
last_modified_at: 2022-06-21 # 이 글을 수정한 날짜.
---

## Summary

- 

## 0. Information

- 2022-06-21 기준 24회 인용

- JCR IF 2020 기준 4.016 (Q1)

- 2021년에 출판된 최신 논문임.
<br>

## 1. Introduction

- 산업과 관련된 빅데이터의 발달과 IoT의 발달로 여러 기계시스템에 대한 PHM의 인기가 점점 증가하고 있다.
- 예전에는 Machine learning을 통한 진단이 주였지만, 이는 사람이 특징 추출을 하거나 다른 고도의 전처리 기술이 필요로 된다.
- 이용 가능한 데이터의 증가로 data-driven 방법이 점점 더 중요해지고 있다.
- 딥러닝 기반의 고장진단이 우수하지만, 두가지 가정이 존재해야함.

  1. 훈련 샘플과 테스트 샘플의 분포가 같아야 한다.
  2. 충분한 레이블 데이터가 있어야 함.

- 기본적인 딥러닝 모델은 weak generalization ability를 가지고 있음.
- 회전체 기반의 기계들은 힘, 속도와 같이 운행조건이 서로 다른 상태로 돌아가게 됨.
- 내재되어 있는 유사성 때문에 두개의 도메인에 존재하는 Shared feature는 domain shift를 다룰 수 있음.
- 하지만 target domain에는 레이블이 없는 경우가 다수임. 그래서 이 논문에서는 unsupervied deep transfer learning(UDTL)에 대해 다룸.
- UDA(Unsuperviesd Domain Adaptation)과 비슷하지만 본 논문에서는 이를 구분하지 않을 것이다.

- 컴퓨터 분야에서는 open source code와 baseline에 대한 정확도 정보가 많지만 고장진단 분야에서는 그렇지 못함
- 사람들은 항상 의심한다. 파라미터 개수가 많아서 정확도가 높은게 아닌 지? - 이러한 문제를 해결해야 한다.
  
  > Zheng, Huailiang, et al. "Cross-domain fault diagnosis using knowledge transfer strategy: A review." Ieee Access 7 (2019): 129260-129290.

- 위의 논문에서 open source data를 제공하고 transfer learning방법에 대한 성능비교를 한다. 하지만 UDTL에 초점을 두고 있지 않다. (Source domain과 Target domain이 같은 분포에 있다.)

- Main Contibution

  1. 훈련에 source 도메인은 얼마나 써야하고, target 데이터는 어떻게 써야하는지를 다룬다.
  2. 데이터를 split하는 방법에 대해 논의한다.
  3. 여러 UDTL을 평가하고 비교한다. 그리고 backbone에 대한 영향, negative transfer에 대한 영향을 다룬다.
  4. Open source code를 제공한다. <https://github.com/ZhaoZhibin/UDTL/tree/master/datasets>
<br>

## 2. Background and definition

### A. Defintion of UDTL

- Source 도메인의 데이터 구성과 Target 도메인의 데이터 구성에 대해 설명 (생략)

<br>

### B. 

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/174751062-578bc48f-1789-475e-9e0d-088f570bd5f9.png" width="600" height="auto">
</p>




## Reference

- Zhao, Zhibin, et al. "Applications of unsupervised deep transfer learning to intelligent fault diagnosis: A survey and comparative study." IEEE Transactions on Instrumentation and Measurement (2021).
