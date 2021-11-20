---
title:  "Class의 사용"
search: false
categories: 
  - Python_MEMO
tags:
  - programming
  - class
  - Python
excerpt: "클래스의 함수적 활용"
---

# python 클래스에 대한 이해
___

> 출처 : https://engineer-mole.tistory.com/190


## 코드의 차이

클래스를 이용하지 않고 함수를 작성한다면 다음과 같이 작성하게 된다.

```py
def Function1(something):
    print("~")
    ...
```

클래스를 사용해서 작성하면 다음과 같다.

```py
class Class1:
    def __init__(self, something):
        self.something = something
    
    def Function1(self):
        print(self.something)
```

## 얻는 이점들

함수만 쓰는게 아니라 클래스를 이용해서 구성한다면 다음과 같은 이점들을 얻을 수 있다.

1. 글로벌 변수를 없애고, 모든 변수를 어떠한 스코프에 소속시킨다. 어떤 scope 바깥에서 변수를 선언하게 되면 난잡해지고 혼란스러울 수 있다.

2. 몇 번이고 재사용 가능하다. 인스턴스(클래스를 실체화한 것)를 여러 번 만들기만 하면 재사용이 쉽다.

3. 코드의 수정을 최소화할 수 있다.

4. 함수 실행 중 함수 자신을 다시 호출하는 처리 등이 가능해진다.

## 인수 self에 대한 이해

```py
class MyStatus:
    def __init__(self,age,name,height,weight):
        self.age = age
        self.name = name
        self.height = height
        self.weight = weight

data = my_status(34,"yamada",170,78)
```

이 코드를 보면, 생성자(constructor)에 해당하는 init함수에 주목해보자. init함수는 인스턴스 생성 시 가장 먼저 실행되는 함수이다. self를 인수로 받고, 함수 내용에 self.age...등 self라는 용어가 등장하고 있다. 이는 MyStatus라는 클래스로 인스턴스가 생성되었을 때(위 코드에서는 'data' 변수)그 자기 자신을 지칭하기 위한 인수이다. 즉, self.age는 data.age가 되는 것이다.  

c++의 클래스를 예로 들어보면 age, name 등의 인수들은

```cpp
class health{
    public:
        int age;
        char name;
        int height;
        int weight;
}
```
처럼 저장이 된다.