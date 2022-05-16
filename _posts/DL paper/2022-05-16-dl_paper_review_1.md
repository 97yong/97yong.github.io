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
last_modified_at: 2022-05-16 # 이 글을 수정한 날짜.
---

## 0. Information

- 2022-05-16 기준 0회 인용

- JCR IF 2020 기준 8.038 (Q1)

- 2022년에 출판된 최신 논문임.
<br>

## 1. Introduction

- Intelligent fault diagnosis(IFD)는 연구 hotspot이 되고 있다. IFD는 <b>자동적으로 특징을 추출하는데 이점</b>을 가지고 있고 사람의 labor를 제거하고 있다.
- 하지만 IFD가 제대로 되려면 두가지를 만족해야한다. (1) 충분한 레이블 데이터 (2) 훈련과 테스트의 같은 분포
  > 이러한 점은 현실에서 제대로 만족하지 않는다.

- 전문가가 큰 양의 데이터를 레이블하는 것은 시간이 많이 들고, IFD는 훈련된 데이터가 아닌 다른 기계나 다른 운영조건하에 적용이 된다. (이를 train과 test 데이터가 다른 분포라고 함)
- Domain Adaptation(전이학습의 한 종류)는 unlabeled data에 대해 성공적으로 적용시켜옴.
  > 학습된 Knowledge는 다른 기계나 다른 운행조건에 있는 기계의 task를 다루는데 일반화된다.
  >> 즉, 운행조건과 관련없는 특징들을 추출해 운행조건이 다름에도 불구하고 좋은 성능을 보일 수 있다.



- Distance metircs도 Domain Adaptation에 직접적인 영향을 미쳤다. 대표적으로는 MMD(Maximum Mean Discrepancy: 최대평균불일치)가 있다.
-  
