---
title:  "Decorator(데코레이터)"
search: false
categories: 
  - Python_MEMO
tags:
  - programming
  - Python
  - function
  
excerpt: "데코레이터에 대해 알아보자"
---

# 데코레이터(decorator)
___ 

## 개념
데코레이터는 함수의 앞과 뒤에서 실행되는 기능을 추가적으로 구현하고 싶을 때 사용한다.

## 형식
```py
def hello_decorator(func):
    def decorated():
        print("hello!")
        func()
        print("nice to meet you!")
    return decorated

@hello_decorator
def hello():
    print("I'm Hyuntae")

hello()

'''
Return :
hello!
I'm Hyuntae
nice to meet you!
'''
```

위의 코드를 살펴보자. 평범함 함수처럼 hello_decorator 라는 함수를 구현했다. 여기서 조금 특이한 점은 인수로서 함수의 이름을 받는다는 것이다. func이라는 함수를 인수로 받아서, hello_decorator 함수 중간에 func()을 실행한 바 있다. 

사용하기 위해서는 다음과 같은 형식을 지켜야 한다.

```py
def 데코레이터_이름(인수함수):
    def 아무이름():
        인수로_받은_함수_전에_실행할_내용()
        인수함수()
        인수로_받은_함수_후에_실행할_내용()
    return 아무이름  #이때 소괄호를 붙이면 안된다.
```

이와 같은 방식을 지키면 된다.

## 사용방식

데코레이터를 사용할 때는 두 가지 방식이 있다. 

### 1. @('at')을 이용

맨 처음 위에서 예시를 들었던 것처럼 데코레이터를 붙일 함수 바로 위에다 @decorator_name 처럼 붙이는 것이다. 

```py
@hello_decorator
def hello():
    print("I'm Hyuntae")

hello()

'''
Return :
hello!
I'm Hyuntae
nice to meet you!
'''
```

이 방식이면 그냥 함수만 호출해도 자연스럽게 데코레이터가 붙어서 실행된다.

### 2. 일반 함수처럼 사용

```py
trace_hello = trace(hello) #데코레이터에 호출할 함수 넣고 저장
trace_hello() #데코레이터 호출

'''
Return :
hello!
I'm Hyuntae
nice to meet you!
'''
```
이 방법의 경우 데코레이터에 먼저 함수를 넣고, 그것을 새로운 함수 trace_hello에 저장한 후 실행해야 데코레이터 + 원래 함수가 실행된다.


## 데코레이터 여러 개 사용

데코레이터를 여러 개 사용하기 위해서는 위의 방식에서 조금만 변형하면 된다. 

### 1번 방법
```py
@decorator1 #which print "decorator 1" ahead of the function
@decorator2 #which print "decorator 2" ahead of the function
def func():
    print("it's function")

func()

'''
return :
decorator 1
decorator 2
it's function
'''
```

### 2번 방법
```py
decorated_func = decorator1(decorator2(func))
decorated_func()

'''
return :
decorator 1
decorator 2
it's function
'''
```

위의 두 방식 모두 decorator 1이 실행된 이후 2가 실행된다. @ method의 경우 위에서부터 차례로 실행된다. 일반 함수처럼 쓰는 method에서는 바깥에서부터 안쪽 순으로 실행된다.

## 참고

데코레이터에서 함수의 이름을 가져올 때는 다음과 같은 방식을 취한다. 

```py
def trace(func):
    def wrapper():
        print(func.__name__, '함수 시작')
        func()
        print(func.__name__, '함수 끝')
    return wrapper 
```

인수를 func으로 받았다면 함수의 이름은 func.__name__으로 불러와서 사용할 수 있다.

