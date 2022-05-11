---
title:  "[논문리뷰] Automation of multi-fault diagnosing of centrifugal pumps using multi-class support vector machine with vibration and motor current signals in frequency domain"
excerpt: "Journal of the Brazilian Society of Mechanical Sciences and Engineering(2018)"

categories:
  - pump
tags:
  - [pump]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
 
date: 2022-05-09 # 글을 처음 작성한 날짜
last_modified_at: 2022-05-11 # 이 글을 수정한 날짜.
---

## 0. Information

- 2022-05-09 기준 29회 인용

- JCR IF 2020 기준 2.220 (Q2)
<br>

## 1. Introduction

  - <u>원심펌프(Centrifugal pump(CP))</u>는 물을 수직으로 전달하는데 사용된다.
  - 전 세계적으로 생산되는 20%의 에너지는 원심펌프를 구동되는데 소비된다! (놀라웠다..)

    > 20% of the energy produced globally is said to be consumed in running CPs.

  - 원심펌프 고장들은 크게 기계적인 결함과 유동에 의한 결함으로 분류된다. (mechanical faults & fluid-flow-induced faults)
  - 이러한 결함들은 서로 의존적이다. (하나가 고장나면 다른 고장이 일어나도록 자극(stimulate)한다.) 자세한 것은 Section 5에서 다룬다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/167804361-f26a666f-a8c3-438c-9f01-e76570791116.png" width="800" height="auto">
</p>

  - Table 1 에는 원심펌프 결함의 원인과 영향이 적혀있다.
    - <b>Suction blockage</b><br>
      <b>(원인)</b> 깨끗하지 않은 액체와 표면으로 인한 단면적 감소<br>
      <b>(영향)</b> Discharge re-circulation, cavitation, 부품들의 crack 등<br><br>
    - <b>Discharge blockage</b><br>
      <b>(원인)</b> BEP(Best Efficiency Point) 이하 유동<br>
      <b>(영향)</b> Suction re-circultation<br>
      > Suction blockage는 Discharge부분에 유체가 방향이 바뀌는 현상을 발생시키고, Discharge blockage는 Suction부분에 유체가 방향이 바뀌는 현상을 발생시킴!<br>
    - <b>Impeller defects</b><br>
      <b>(원인)</b> Impeller를 주조할 때 오차, cavitation, 재료부식, 피로<br>
      <b>(영향)</b> Unbalance, pseudo-flow re-circulation(Terminology 참고), 소음 등등<br><br>
    - <b>Pitted cover plate</b><br>
      <b>(원인)</b> 제조 결함, cavitation에 의한 부식과 재료 부식에 의한 손상<br>
      <b>(영향)</b> 난류유동<br><br>
    - <b>Dry run</b><br>
      <b>(원인)</b> 원심펌프에 불충분한 물<br>
      <b>(영향)</b> 베어링, seal 손상, 소음, 진동<br><br>
  
  - 이러한 결함들이 결합해서 나타나면 Bubble이 생기게 되는데 이는 CP의 수두 성능을 떨어뜨리고 내부 부품에 손상을 가한다.<br>
  - 기계적 결함은 원심펌프의 속도와 직접적으로 연관되어 있어서 진단하기 쉬운 반면 유동에 의해 생기는 결함은 진단하기 어렵다.<br>
  - 원심 펌프를 진단하기 위해 신호(signal)을 선택하는 것은 중요하다. 자주 사용되는 신호는 <u>vibration, motor line current, acoustic emission signals</u>이다.
    > 결함이 모터의 하중을 바꾸기 때문에 motor line current도 변한다.
  - 많은 연구자들은 Time domain에 대한 신호를 사용했는데, 주파수 영역의 신호는 waveform을 간단하게 해주는 등 여러 이점이 있다.
  
### Main Contribution
  - 기계적, 유체역학적 결함에 대해서 독립적으로 그리고 조합적으로 나타나는 결함을 분류하려는 시도
  - 원심펌프의 suction & disccharge blockage들의 여러가지 심각도를 isolate 한다.
  - 여러 운행조건에도 강건한 방법론을 제시
  - 주파수 대역의 resolution에 대한 비교 study
  - 진동신호와 직류전류신호 조합을 사용하는 것에 대한 효과
  - SVM을 통한 3가지 결함을 분류하는 방법론 개발
  
<br>

## 2. CP fault analysis test setup

 - Oberdorfer 60P 원심펌프 사용
 - 원심 펌프는 3가지로 운전된다. (1. impeller와 cover plate 모두 healthy / 2. impeller만 fault / 3. cover plate만 fault)
 - 총 33개의 고장으로 크게 10가지로 분류된다.
   > 1. healthy pump / 2. suction blockage faults / 3. discharge blockage faults / 4. impeller defects / 5. combination of impeller defects and suction blockages / 6. combination of impeller defects and discharge blockages / 7. pitted cover plate faults / 8. combination of pitted cover plate faults and suction blockages / 9. combination of pitted cover plate faults and discharge blockages / 10. dry-run faults
 - Suction & discharge blockages는 B0~B5(유동의 양에 따라)로 나누어 밸브를 조절하면서 고장을 만들어주었다.
 - Impeller 고장은 notch를 주었다. (vane당 2개, 비대칭적으로)
 - 진동신호는 triaxial accelerometer를 통해, 직류전류신호는 3개의 probe를 통해 얻어진다.
 - 펌프 운전조건은 30~65Hz로서 5Hz 단위로 운전되었다.
 - 샘플링 주파수를 달리해서도 데이터가 얻어진다.(5000Hz, 20000Hz)
<br>

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/167822366-80da2132-bc44-4248-bb5c-3393aa725d54.png" width="600" height="auto">
</p>

 - 펌프 구조도는 위와 같음

### 2.1. Interdependence of faults

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/167826653-36704745-94df-46da-8534-c0a80df7bc71.png" width="600" height="auto">
</p>
 - 펌프의 기계적, 유체역학적 고장은 서로 관련이 있다.
 - 예를 들어 impeller 고장은 압력차이로 인해 유동이 결함을 통해 흘러들어가 흐름을 방해한다. 그래서 bubble을 생성한다.
 - Bubble이 터질 때 <b>Shock Wave</b>를 만들어 내는데, 이는 고체 표면에 영향을 미친다.
 - 이로써 기계적, 유체역학적 고장은 악순환을 만들어낸다.
<br>

## 3. CP fault diagnosis methodology

 - SVM이 사용되었고, 자세한 설명은 생략 (SVM에 대한 설명은 다른 포스트를 참고하는 것이 좋을 듯하다. / 나중에 작성예정)
 - Kernel로는 Gaussian RBF커널이 사용되었다.
<br>

## 4. Feature selection and effect of the sampling rate on the fault predictions

 - <u>Raw data는 high dimensionality를 가지고 있어</u> 적절한 통계적 특징을 도출해야한다.
 - 본 논문에서는 평균, 분산, skewness, kurtosis 등... 여러가지 통계적인 수치를 활용하였고 최종적으로 <b>wrapper model</b>을 이용해 feature selection을 하였다.
 - 특정 Task를 통해 평균, 표준편차, 표준편차의 역수가 feature로 선택되었고 99.2%의 성능을 내었다.
 - 데이터는 high-resolution으로 얻어진 것으로 이행되었고, low-resolution과 비교했을 때 8%정도 성능이 더 좋다.
   > 이는 샘플링 주파수가 높은 데이터로 분류를 진행했을 때 더 높은 성능을 보이는 것을 알 수 있다.

### 4.1 Data required for training and testing

 - Train과 Test 데이터의 비율을 달리해 실험을 했다.
 - 50/50 비율이 가장 일반화를 잘한다고 고려해 논문에서는 이를 선택했다.
<br>

## 5. Frequency-domain prediction performance: results and discussion
### 5.1 Fault classification cases and results

 - 각각 Task를 달리해서 구체적인 결과가 적혀있음.
 - 이에 대한 결과는 논문을 참고바람

<br>

## Terminology

 - re-circulation: Impeller의 inlet과 outlet의 끝에서 유체가 방향전환(turnaround)하는 것을 의미한다.
 - throttle valve: 유량을 조절하는 밸브
 - pseudo-flow re-circulation: Impeller가 회전하는 것을 방해하는 반대 유동의 흐름
 - priming: 원심 펌프를 기동시킬 때 내부에 물을 가득 채우는 일
 - line current: 직류 전류에서 측정된 양

<br>

## Reference
 - Rapur, Janani Shruti, and Rajiv Tiwari. "Automation of multi-fault diagnosing of centrifugal pumps using multi-class support vector machine with vibration and motor current signals in frequency domain." Journal of the Brazilian Society of Mechanical Sciences and Engineering 40.6 (2018): 1-21.
