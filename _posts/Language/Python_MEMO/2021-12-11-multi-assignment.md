---
title:  "Multi-Assignment"
search: false
categories: 
  - Python_MEMO
tags:
  - programming
  - Python
excerpt: "다중 할당의 특징과 주의점"
---

# 파이썬 다중 할당에 대해서
___

## 개념
다중 할당(multi-assignment)이란, 2개 이상의 값을 2개 이상의 변수에 동시에 할당하는 것을 말한다. 

## 형태
> var1, var2 = formula1, formula2  

이런 형태로 표현할 수 있다.

## 연산 과정  

다중 할당은 단순히 var1 = num1; var2 = num2이 두 줄의 코드를 하나로 합친 것이 아니다. 처리 과정은 다음과 같다.

```
Result1 = formula1
Result2 = formula2
var1 = Result1
var2 = Result2
```
이를 보면 우측에서 먼저 계산을 다 끝마치고 난 이후에 좌측 변수들에
그 계산값을 할당한다는 것을 알 수 있다.   

## 주의 사항

### 계산 과정에 따른 문제점

```py
#when multi-assign
x = 1, y = 2
x, y = y, x + y
result : x = 2, y = 3

#it is because process is
A = y
B = x+y
x = A
y = B

#repeating single assign
x = 1, y = 2
x = y
y = x + y
result : x = 2, y = 4
```
위의 code block을 보면 코드를 그저 두 줄로 나누었을 뿐인데 값이 달라진다. 그 이유는 앞서 설명했던 것처럼 multi-assign을 진행하기 이전에 우측에서 모든 equation을 계산한 이후에 값을 할당하기 때문이다. Q13에서 나타났었던 문제도 살펴보자.

```py
rev, rev.next = node, rev
#This is same as
A = node
B = rev
rev = A 
rev.next = B
```
위의 코드를 보면
- A에 노드가 할당된다. 
- B에 rev 연결리스트의 head 노드인 rev가 할당된다.
- "rev = A"에 의해 새로 넣을 노드가 "전"head 노드인 rev에 할당된다.
- "rev.next = B"에 의해  새로 넣을 노드는 "전" 노드인 rev(rev = A 이전)를 가르킨다.

다중 할당의 특성으로 인해 이런 방식으로 계산된다.

### 참조 대상 중복
```py
# rev = 1, slow = 2->3. slow is linked list and slow.next means 3

#right case
rev, rev.next, slow = slow, rev, slow.next

#wrong case
rev, rev.next = slow, rev
slow = slow.next
```
Right case를 보면 다중 할당 시에 모든 작업이 동시에 일어나기 때문에 중간 과정 없이 한 번이 트랜잭션으로 끝나게 된다. 먼저 rev = 2->3, rev.next = 1에 의해 rev = 2->1이 되고, slow = slow.next에 의해 slow = 3이 된다.  
__Result : rev = 2->3, rev.next = 1, slow = 3__

하지만 Wrong case처럼 코드를 나눠 처리하는 경우 문제가 발생한다. rev와 rev.next의 값은 위와 동일하다. 문제는 rev = slow이다. 여기서 rev와 slow는 동일한 참조가 되었기 때문에 slow 역시 slow = 2->1이 된다. 그래서 slow = slow.next는 slow = 1이 된다.  
__Result : rev = 2->3, rev.next = 1, slow = 1__

따라서 multi-assign할 때는 혹시 예상치 못하게 동일한 값을 참조하는 문제가 발생하지는 않았는지, 특유의 연산 과정에 따른 설계 미스가 발생하지 않았는지 유심히 생각해보아야 한다.