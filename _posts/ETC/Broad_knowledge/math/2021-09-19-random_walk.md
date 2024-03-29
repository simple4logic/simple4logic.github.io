---
title:  "Random Walk"
search: false
categories: 
  - Broad_knowledge
tags:
  - math
  - probability_theory
excerpt: "랜덤워크란?"
toc : true
---

## 기본 개념

말그대로 주어진 공간에서 매 순간 랜덤으로 이동하는 것을 말한다.  
임의의 방향으로 향하는 연속적인 걸음을 나타내는 수학적 개념.  
<br>

## 특징
- 1차원(직선)에서의 랜덤워크의 경우  
시간에 따른 기댓값(평균) = 0 유지  
분산은 시간에 비례하여 증가. 즉, n번째 walk이라면 분산은 n (=표준편차가 √n).

<center>

![image](https://user-images.githubusercontent.com/68508521/133915732-b6c0c6b8-a0dc-472b-85aa-fd55e2d207cb.png)

</center>
<br>

- 2차원에서의 랜덤워크  

<center>

![image](https://user-images.githubusercontent.com/68508521/133915737-eacf1f81-2183-4470-9de9-2d65be4b939d.png)  

</center>
<br>

- 3차원에서의 랜덤워크  

<center>

![image](https://user-images.githubusercontent.com/68508521/133915752-299d0e3a-bd0c-4c24-aace-2b16b7426429.png)

</center>

<br>

## 추가적인 논의점
수열 자체 Sn만 본 결과는 단조롭다. 그렇기에 랜덤워크 이론에서는 경로 전체에 집중한다(즉, 수열 S1, S2, S3, ⋯). 

- n시간 후에 점이 원점에서 가장 멀리 떨어졌던 거리는 어느 정도일까?  
A. 이에 대한 답은 반복 로그의 법칙(law of the iterated logarithm)에 따르면   
 ![image](https://user-images.githubusercontent.com/68508521/133915872-152b3ce7-f3eb-4021-99d1-f81a7f3c300f.png) 이 된다.

- 어느 순간 이후로 원점을 지나지 않는 것이 가능할까?  
A. (확률 1로) 불가능하다.


수열 자체가 아닌 경로들의 전반적인 특징을 파악하는 것이 랜덤워크 이론의 주된 흐름이 된다. 특이한 점은 랜덤 워크에 대한 적지 않은 질문들은 확률이 0 아니면 1로 주어지는 0-1 법칙(zero-one law)을 따른다는 점.

<br>

## 타 분야에서의 사용
- 브라운 운동 모델  

- 재무관리의 효율적 시장 가설  
>효율적 시장이란 증권에 대한 정보가 신속, 정확하게 가격에 반영되고 거래비용이나 세금같은 시장마찰 요인이 존재하지않아 거래가 원활하게 이루어지며 자금이 적재적소에 배분되기 때문에 모든 자산은 공정한 가격에 거래되어 정상이익 이상의 수익을 얻을 수 없는 시장이다. 즉, 고/저평가되는 자산이 없다는것.  
 정보의 반영 속도에 따라 약형, 준강형, 강형 효율적 시장으로 나뉘는데, 랜덤워크 모형이 약형 효율적 시장의 가정으로 등장한다. 약형 효율적 시장은 증권의 모든 과거정보가 가격에 반영되어 있으므로 주가행태 분석같은 기술적 분석으로는 비정상수익을 얻을 수 없다. 여기에서 증권의 가격은 랜덤워크 모형으로 움직이며 이에 대한 예측은 불가능하다.  
  따라서 과거의 주가 정보 분석으로는 비정상수익을 얻을 수 없는 것이다. 특정 투자자가 과거정보 분석으로 비정상수익을 얻었다 하더라도 이는 우연의 일치이며 반복적으로 수행할 수 있는 표준화된 분석으로 비정상 수익을 얻은 것이 아니기 때문에 이는 약형 효율적 시장을 부정하는 사례가 될 수 없다.

<br>

  ## 더 알아보기
  ___

  1. 반복로그  
  https://ko.wikipedia.org/wiki/%EB%B0%98%EB%B3%B5_%EB%A1%9C%EA%B7%B8

  2. 콜모고로프 0-1 법칙(Kolmogorov's zero-one law)  
  https://bayestour.github.io/blog/docs/bc/0103
