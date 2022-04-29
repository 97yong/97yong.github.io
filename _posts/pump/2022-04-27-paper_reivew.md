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
![image](https://user-images.githubusercontent.com/104422044/165876908-e70005da-8aab-497f-afec-350058d0800d.png)<br>
 - 본 논문의 실험에서는 Monoblock 원심펌프가 사용됨.
 - <details><summary>Monoblock 이란?</summary>
   <p>
     Mono는 single을 의미한다. Monoblock은 수평 다단 펌프를 의미한다.
  </p>
  </details>
 - 
