---
title:  "전위 연산자와 후위 연산자"
search: false
categories: 
  - C++_MEMO
tags:
  - programming
  - Operator
  - C++
excerpt: "Prefix & Postfix"
toc : true
---

# Prefix, Postfix에 대해서
___

## 개념
Prefix와 Postfix : 각각 전위 연산자, 후위 연산자이다. 
우리가 일반적으로 코드상에서 ++a라고 쓰는 것이 전위 연산자이고, a++라고 쓰는 것이 후위 연산자이다. 둘의 차이는 우선 순위에 있다.

![image](https://user-images.githubusercontent.com/68508521/135743936-19d8fd76-5477-48fb-a636-e2d74c332383.png)  

해당 그림을 참고하며 다음의 예시를 보자. 

## example 1
a=b=1인 상태에서 다음을 실행해보자.
> printf("a=%d 이고 b=%d", ++a, ++b);  
출력값: a=2 이고 b=1  
printf("a= %d 이고 b=%d", a, b);  
출력값 : a= 2 이고 b=2

a는 print되기 이전에 먼저 1 증가한 상태로 함수에 들어가고, b는 함수에 들어가서 출력된 이후에야 1 증가한다. 그래서 나중에 한 번더 print해보면 둘다 2인 것을 확인할 수 있다.  

이를 적용한 다른 case를 한 번 보자.

## example 2  

<script src="https://gist.github.com/simple4logic/2f28e04193bdb390cc79fb6a0db830fe.js"></script>

코드 실행결과는 다음과 같다.

```
postfix
postfix
postfix
postfix
prefix
prefix
prefix
```

일반적으로 루프문에서는 다 후위연산자를 쓴다. while(n--)처럼 postfix로 하면 우리가 일반적으로 의도하는 n번만큼의 반복을 해주지만, while(--n)처럼 prefix로 하면 n-1번만큼의 반복만 해서 의도와 달라지게 된다.