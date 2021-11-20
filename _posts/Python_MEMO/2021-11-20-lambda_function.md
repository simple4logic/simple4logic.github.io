---
title:  "Lambda Function"
search: false
categories: 
  - Python_MEMO
tags:
  - programming
  - function
  - Python
excerpt: "함수를 간편히 사용해보자"
---

# 람다 함수의 간단한 이해
___

## 개념
람다 표현식은 식별자(함수의 이름) 없이 실행이 가능한 함수를 말한다. 함수 선언 없이도 하나의 식으로 함수를 단순하게 표현 가능하다.

## 형태  

> lambda 인자 : 표현식

처럼 표현할 수 있다.

## 예시

두 수를 더하는 람다 함수를 예로 들어보자.
```py
def hap(x, y):
    return x + y

hap(10, 20)
# return 30

# 이 함수를 람다식으로
(lambda x, y: x+y)(10, 20)
# return 30
```
  
<br>

Q3에서 등장한 lambda 함수에 대해 살펴보자.

```py
let = ["let1 art can","let2 own kit dig","let3 art zero"]

let.sort(key=lambda x:(x.split()[1:], x.split()[0]))
```

list의 메소드 함수 중 sort 함수는 인자로서 key=Function을 받는다. sort(key=FunctionName)으로 입력하면 된다.  
__list의 인자들을 해당 Function에 넣고, 그 리턴값에 따라서 sorting 하는 방식__ 이다.

1. 먼저, "let1 art can","let2 own kit dig","let3 art zero"는 각각 함수 lambda x:(x.split()[1:], x.split()[0])의 인자 x로서 들어간다.

2. x.split()에 의해 첫번째 원소인 string "let1 art can"은 [let1, art, can]으로 쪼개진다. 다른 원소들도 마찬가지.

3. 그 후 [1:]에 의해 "art can", "own kit dig", "art zero"만 남게 되고 이 원소들 간에 sort 함수가 작동하게 된다.

4. 두번째 return 값인 x.split()[0]은 동일 문자일 때 sort할 두번째 기준이다.