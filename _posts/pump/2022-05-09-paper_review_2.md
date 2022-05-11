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
last_modified_at: 2022-05-09 # 이 글을 수정한 날짜.
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
    - Suction blockage: <u>(원인)</u> 깨끗하지 않은 액체와 표면으로 인한 단면적 감소 <u>(영향)</u> Discharge re-circulation, cavitation, 부품들의 crack 등
    - Discharge blockage: <u>(원인)</u> BEP(Best Efficiency Point) 이하 유동 <u>(영향)</u> Suction re-circultation
    > Suction blockage는 Discharge부분에 유체가 방향이 바뀌는 현상을 발생시키고, Discharge blockage는 Suction부분에 유체가 방향이 바뀌는 현상을 발생시킴!
    - Impeller degects: <u>(원인)</u> Impeller를 주조할 때 오차, cavitation, 재료부식, 피로 <u>(영향)</u> Unbalance, pseudo-flow re-circulation(Terminology 참고), 소음 등등
    - Pitted cover plate: <u>(원인)</u> 제조 결함, cavitation에 의한 부식과 재료 부식에 의한 손상  <u>(영향)</u> 난류유동
    - Dry run: <u>(원인)</u> 원심펌프에 불충분한 물 <u>(영향)</u> 베어링, seal 손상, 소음, 진동
  
  - 이러한 결함들이 결합해서 나타나면 Bubble이 생기게 되는데 이는 CP의 수두 성능을 떨어뜨리고 내부 부품에 손상을 가한다.
  
<br>

## 2. Experimental studies

### 2.1. 실험 세팅

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/167360720-15b52e3b-8e06-4382-961a-4d4e4ba899b6.png" width="400" height="auto">
</p>


<br>
 
## 6. Result and Discussion
  



## Terminology

 - re-circulation: Impeller의 inlet과 outlet의 끝에서 유체가 방향전환(turnaround)하는 것을 의미한다.
 - throttle valve: 유량을 조절하는 밸브
 - pseudo-flow re-circulation: Impeller가 회전하는 것을 방해하는 반대 유동의 흐름
 - priming: 원심 펌프를 기동시킬 때 내부에 물을 가득 채우는 일

<br>

## Reference
 - Rapur, Janani Shruti, and Rajiv Tiwari. "Automation of multi-fault diagnosing of centrifugal pumps using multi-class support vector machine with vibration and motor current signals in frequency domain." Journal of the Brazilian Society of Mechanical Sciences and Engineering 40.6 (2018): 1-21.
