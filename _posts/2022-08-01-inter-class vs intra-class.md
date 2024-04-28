---
title: "class variance 개념 정리"
date: 2022-08-01 00:00:00
categories: [AI]
tags: [class variance] # TAG names should always be lowercase
---

## inter-class variace vs inter-class variance

데이터 분석에서 데이터 분산을 표현할 때는 다음과 같은 용어를 사용한다.

- **inter-class** variance: **class 간의** 분산
- **intra-class** variance: **class 내부의** 분산

예를 들어 아래의 그림을 보자!!  
<img src="/assets/img/class_variance.png" alt="illustration of class variance">

**a) inter-class variance가 크고, intra-class variance가 작은 경우**

- 빨간색, 파란색 두 클래스가 서로 떨어져 있음 -> inter-class variance가 크다.
- 같은 색의 점들이 모여 있음 -> intra-class variance가 작다.

**b) inter-class variance가 작고, intra-class variance가 큰 경우**

- 빨간색, 파란색 두 클래스가 가까이 있음 -> inter-class variance가 작다.
- 같은 색의 점들이 비교적 떨어져 있음 -> intra-class variance가 크다.
  <br/><br/><br/>

> reference: <https://www.statisticalaid.com/intra-class-vs-inter-class-correlation/>
