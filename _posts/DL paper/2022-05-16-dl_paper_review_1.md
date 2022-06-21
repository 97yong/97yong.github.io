---
title:  "[논문리뷰] Weighted quantile discrepancy-based deep domain adaptation network for intelligent fault diagnosis"
excerpt: "Knowledge-Based Systems (2022)"

categories:
  - DL Paper
tags:
  - [paper, deeplearning]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
use_math: true

date: 2022-05-16 # 글을 처음 작성한 날짜
last_modified_at: 2022-06-21 # 이 글을 수정한 날짜.
---

## 0. Information

- 2022-05-16 기준 0회 인용

- JCR IF 2020 기준 8.038 (Q1)

- 2022년에 출판된 최신 논문임.
<br>

## 1. Introduction

- Intelligent fault diagnosis(IFD)는 연구 hotspot이 되고 있다. IFD는 <b>자동적으로 특징을 추출하는데 이점</b>을 가지고 있고 사람의 labor를 제거하고 있다.
- 하지만 IFD가 제대로 되려면 두가지를 만족해야한다. (1) <u>충분한 레이블 데이터</u> (2) <u>훈련과 테스트의 같은 분포</u>
  > 이러한 점은 현실에서 제대로 만족하지 않는다.

- 전문가가 큰 양의 데이터를 레이블하는 것은 시간이 많이 들고, IFD는 훈련된 데이터가 아닌 다른 기계나 다른 운영조건하에 적용이 된다. (이를 train과 test 데이터가 다른 분포라고 함)
- Domain Adaptation(전이학습의 한 종류)는 unlabeled data에 대해 성공적으로 적용시켜옴.
  > 학습된 Knowledge는 다른 기계나 다른 운행조건에 있는 기계의 task를 다루는데 일반화된다.
  >> 즉, 운행조건과 관련없는 특징들을 추출해 운행조건이 다름에도 불구하고 좋은 성능을 보일 수 있다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/167419716-bd7da8f8-0830-4c35-b2e3-2fc21bff657a.png" width="600" height="auto">
</p>

- Distance metircs도 Domain Adaptation에 직접적인 영향을 미쳤다. 대표적으로는 MMD(Maximum Mean Discrepancy: 최대평균불일치)가 있다.
- 위의 MMD는 <https://97yong.github.io/dl%20study/mmd/> 여기를 참고하자.
- 하지만 MMD는 Time Complexity를 크게 가짐 \\(O(n^2 + 2nm + m^2)\\)
- 많은 기계 데이터들은 다루기가 어렵고, Gaussian kernel parameter도 튜닝되어야한다.
- MMD와 비슷한 CMD가 있지만 공학적인 task에서는 사용이 잘 되지 않는다.

- 본 논문에서는 MMD와 CMD에 영감을 받아 WQD(Weighted Quantile Discrepancy)를 제안한다.
- Time Complexity는 \\(O(n + m)\\)으로 줄어들었다. 또한 더 정확하다.

- <b>Main Contribution</b>
  - WQD는 디자인 되었고 MMD, CMD와 비교했을 때 더 정확하고 빠르다.
  - Dynamic WQD의 weight는 high-level의 feature에 따라 업데이트된다. 또한, customize도 할 수 있다.
  - 손실함수는 Network와 결합되었다. 그렇기에 MMD방식보다 다양한 딥러닝 프레임워크에 적용되기 더 쉽다.
<br>

## 2. Related work

### 2.1. Conventional IFD methods
 - ANN, SVM, Random forest
 - 이러한 shallow한 IFD는 복잡한 공학적인 상황에 적합하지 않고 딥러닝 방법이 더 적합하였다.
 - 따라서 CNN, deep belief networks, ResNet-based 접근 등이 개발되었다.

### 2.2. Domain adaptation methods
 - 도메인 적응은 도메인 shift를 다루는데 성공적인 적용방법이었다.
 - feature-based methods: 거리와 같은 방법을 사용하여 소스와 타겟의 분포를 줄였다.
 - GAN-based methods: 손실함수를 최대화 함으로써 도메인 불변의 feature를 만들도록한다. (표현이 조금 이상함)
   > 도메인 discriminator 앞에 GRL(Gradient Reversal Layer)를 붙여 Feature Extractor가 도메인을 잘 분류하지 못하게 한다.(GRL의 효과로 -가 붙여서 역전파가 된다.) 이에 따라 도메인 불변의 특징을 추출할 수 있게 된다.

 - MMD를 사용한 Domain Adaptation관련 논문

>Lu, Weining, et al. "Deep model based domain adaptation for fault diagnosis." IEEE Transactions on Industrial Electronics 64.3 (2016): 2296-2305. <b>이 논문이 고장진단에서 최초로 MMD기반의 Domain adaptation이 채택되었다고 한다.</b>
<br>

> Guo, Liang, et al. "Deep convolutional transfer learning network: A new method for intelligent fault diagnosis of machines with unlabeled data." IEEE Transactions on Industrial Electronics 66.9 (2018): 7316-7325.
<br>

> Yang, Bin, et al. "An intelligent fault diagnosis approach based on transfer learning from laboratory bearings to locomotive bearings." Mechanical Systems and Signal Processing 122 (2019): 692-706.
<br>

 - DANN 관련 진단 논문

> Han, Te, et al. "A novel adversarial learning framework in deep convolutional neural network for intelligent diagnosis of mechanical faults." Knowledge-based systems 165 (2019): 474-487.
<br>

> Li, Yibin, et al. "Intelligent fault diagnosis by fusing domain adversarial training and maximum mean discrepancy via ensemble learning." IEEE Transactions on Industrial Informatics 17.4 (2020): 2833-2841. (DANN+MMD)
<br>

> Zhao, Ke, et al. "Joint distribution adaptation network with adversarial learning for rolling bearing fault diagnosis." Knowledge-Based Systems 222 (2021): 106974. (DANN+MMD)

## 3. Theoretical foundation

### 3.1. Domatin Adaptation problem

- 전통적인 모델들은 레이블된 데이터로 훈련되고 같은 분포에 대해 레이블이 없는 데이터로 전이되었지만, 현실적인 상황에서 도메인 adaptation 문제는 분포가 다르다. 저자들은 이러한 상황에서 문제를 풀고자 하고 다른 운행조건안에 generalized 되도록 하는 모델을 만들어 해결하고 한다.
- 기본적으로 Domain Adaptation 문제에서 source 도메인에 대한 분포와 target 도메인에 대한 분포는 다르다고 가정한다.
<br>

### 3.2. Basic principle of MMD

- p와 q분포로 부터 X와 Y를 random variable이라고 생각할 때, 두 분포 사이에 MMD를 정의할 수 있다.
- MMD는 p와 q의 분포 사이에 discrepancy를 측정한다.
<br>

## 4. The proposed model

### 4.1. Weighted quantile discrepancy

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/174722053-0a0f753d-c4e3-4f5c-bd86-315ecbbd30f7.png" width="400" height="auto">
</p>

- input data에 대해 타우번째 quantile의 분포가 Q이다. 또한, Hilbert를 사용하지 않고 프사이를 사용하였는데, 이는 추가적인 제약조건 없이 linear나 non-linear 변환이 될 수 있다.
- 타우는 (0,1)로 정해질 수 있다.

- Weighted Quantile(WQ)는 모든 quantile level들을 평균한 것인데, 각 quantile마다 weight를 주어 계산하게 된다.

  1. space map에서 projection vector을 얻는다.
  2. 주어진 quantile 수치에 대해 두개의 dataset의 quantile value 사이에 제곱을 계산한다.
  3. Weighted sum을 계산한다.

### 4.2. Deep weighted quantile domain adaptation network(DWQDAN)

- 모델은 전체적으로 5개로 이루어진다. (전처리 과정, shared 신경망, 고장 분류기, 도메인 판별기, 분포 discrepancy)
- 전처리는 Wavelet transform을 통해 이미지로 만들어진다.

  > 개인적으로 신기했던 점: WQ를 하기 위해 새로운 layer를 만들어 나온 노드에 대해서 loss를 계산 (그림 4에서 보면, WQ의 loss를 계산하기 위해 만들어진 layer의 node에 따라 성능을 비교한 것을 볼 수 있음 - 256의 node가 가장 좋았음.)

## 5. Result

- result와 conclusion은 

## Reference

- Fan, Zhenhua, et al. "Weighted quantile discrepancy-based deep domain adaptation network for intelligent fault diagnosis." Knowledge-Based Systems (2022): 108149.
