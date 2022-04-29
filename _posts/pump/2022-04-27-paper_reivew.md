---
title:  "[논문리뷰] Vibration based fault diagnosis of monoblock centrifugal pump using decision tree"
excerpt: "Expert Systems with Applications(2010)"

categories:
  - pump
tags:
  - [pump]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
 
date: 2022-04-27 # 글을 처음 작성한 날짜
last_modified_at: 2022-04-28 # 이 글을 수정한 날짜.
---

## 0. 들어가기 앞서
---

- Sakthivel, N. R., V. Sugumaran, and SJESwA Babudevasenapati. "Vibration based fault diagnosis of monoblock centrifugal pump using decision tree." Expert Systems with Applications 37.6 (2010): 4040-4049.

- 2022-04-27 기준 220회 인용

- JCR IF 2020 기준 6.954 (Q1)

- 2010년에 출판된 오래된 논문임.
<br>

## 1. 서론
---

  - Centifugal pump(원심펌프)는 산업에서 중요하고 이용이 증가함에 따라 연속적인 모니터링이 필요
  - 펌프의 특성에 직접 영향을 미치는 **베어링, 실, 임펠러**는 아주 중요한 부품
  - 진동신호는 원심 펌프를 모니터링하는데 널리 이용
  
  - 본 논문에서는 ***<span style="color:blue"><u>bearing fault (BF), seal fault (SF), impeller fault (IF), bearing and impeller fault (BFIF), cavitation (CAV)</u></span>*** 5가지의 고장이 사용됨.
  - Decision Tree C4.5 algorithm이 사용됨 (2010년 당시 특징추출과 분류가 우수했음)
<br>

## 2. Experimental studies
---
### 실험 세팅
![image](https://user-images.githubusercontent.com/104422044/165876908-e70005da-8aab-497f-afec-350058d0800d.png)<br>
 - 본 논문의 실험에서는 Monoblock 원심펌프가 사용됨.
 - <details><summary>Monoblock 이란?</summary>
   <p>
     Mono는 single을 의미한다. Monoblock은 수평 다단 펌프를 의미한다.
   </p>
   </details>
 - Cavitation을 시각화하기 위해 아크릴 파이프가 사용, 진동센서를 수집하기 위해 Accelerometer는 pump inlet부분에 사용.<br>

### 실험 절차
 - 2880 rpm으로 다른 delivery head를 가진채로 반복실험을 하였음.
 - Current: 11.5A / Head: 20m / Discharge: 392I/s / Power: 2hp
 - 가속도 센서에 대해 샘플링주파수는 24kHz, 샘플길이는 1024 (길이가 길수록 통계적인 측정에 의미가 있으나, 길이가 많이 길게되면 컴퓨터 연산시간 증가 - 따라서 최적의 길이 선택) <br>

![image](https://user-images.githubusercontent.com/104422044/165884278-03483f67-6515-49ee-af5c-7665c9c1adb3.png)<br>
 - 위 그림은 시간 도메인에서 펌프의 진동신호를 나타냄.
 - bearing fault (BF), seal fault (SF), impeller fault (IF), bearing and impeller fault (BFIF), cavitation (CAV) 그리고 normal condition 총 6개의 라벨을 가짐

#### Bearing Fault
 - 결함은 wire cut을 이용하여 만들어졌음.
 - Outer Race Fault 즉, 외륜결함을 내어 신호를 생성
 - 베어링 결함에 대한 여러 고장형태는 다른 논문을 참고하는 것이 도움이 될 것입니다.

#### Seal defect
 - Seal은 두가지 파트로 나뉨. 첫번째는 회전체와 맞닿는 rotating seal part(Inner), 두번째는 고정된 부품과 닿는 stationary seal seat(Outer)
 - 건조한 조건하에 펌프가 작동될 때, 설치시에 무거운 기름이나 윤활제 사용, 설치시에 과도한 압력이 작용할 때 결함이 생김
 - 두개중에 하나를 hammering해서 결함을 내었음

#### Impeller defect

## 용어정리
 - Mono는 single을 의미한다. Monoblock은 수평 다단 펌프를 의미한다.
 - Delivery head: 펌프의 중심으로 부터 물이 전달되는 곳까지의 수직거리
