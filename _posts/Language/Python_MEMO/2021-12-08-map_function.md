---
title:  "map Function"
search: false
categories: 
  - Python_MEMO
tags:
  - programming
  - function
  - Python
  - mapping
excerpt: "map 함수의 다양한 활용"
---

# map 함수의 간단한 이해
___

## 개념
mapping이란 특정 value를 특정 함수에 일대일로 대응시키는 것을 말한다. map함수는 mapping을 해주는 파이썬 함수이다.

## 형태  

> map(function, iterable values)

처럼 표현할 수 있다.  

첫 번째 매개변수로는 함수가 오게 되며,  
두 번째 매개변수로는 반복 가능한 자료형(리스트, 튜플, 딕셔너리 등)이
오게 된다.  

map함수의 return 값은 map이란 별개의 객체이기 때문에 list나 tuple형으로 변환시켜야 한다.  

입력한 자료형 모드를 입력한 함수에 통과시켜 그 모든 리턴값을 반환한다.

## 예시 #1

두 리스트의 원소들을 각각 곱해서 리턴하는 코드를 작성해보자. 곱할 대상은 리스트 a와 b이다.

1. For loop를 이용해 직접 곱하는 경우
```py
result = []
for anum in a:
    for bnum in b:
        result.append(anum * bnum)
```

2. List Comprehension을 이용하는 경우
```py
result = [a[i] * b[i] for i in range(len(a))]
```

마지막으로 map함수를 이용한 경우이다.

3. map 함수를 이용하는 경우
```py
result = list(map(lambda x,y : x*y, a, b))
#x, y를 인수로 하는 lambda function을 작성해서 a, b를 iterate 시켰다. 
```

람다함수를 map function 안에 구현해 놓는다면 함수를 따로 번거롭게 정의해서 쓰지 않고 짧고 간단하게 표현할 수 있다.

map 함수와 lambda function을 같이 사용한 다른 다양한 예제
> https://tykimos.github.io/2020/01/01/Python_Lambda_Map/

  
## 예시 #2
### input().split() 과 map() 함수

> 참고 : https://dojang.io/mod/page/view.php?id=2286

input() 함수로 받은 입력을 split() 했을 때 이를 다루기 쉬운 자료형으로 어떻게 바꾸는지 알아보자.

```py
>>> a = input().split()
10 20 (입력)
>>> a
['10', '20']
```

split() 함수는 기본적으로 문자열을 쪼개는 함수이기 때문에 자르고 난 결과물이 int형이 아니라 str형으로 간주되어 qutation mark가 붙게 된다. 그래서 활용하기에 까다로운 형태이므로, 이를 다시 숫자로 바꾸려고 한다. 이때 map 함수를 이용해서 해당 value들에 int 함수를 씌워주면 된다.

```py
>>> a = map(int, input().split())
10 20 (입력)
>>> a
<map object at 0x03DFB0D0>
>>> list(a)
[10, 20]
```

위 코드는 앞서 말한대로 int 함수와 iterable한 value인 list를 map 함수에 넣은 모습이다. 다만 a를 그대로 print하려고 하면 a는 map 객체인 상태이기 때문에 list나 tuple같은 값을 바꾸어 주어야 한다. 위 코드에서는 list로 바꾸어주어서 정상적으로 의도한 값이 출력되는 것을 볼 수 있다.