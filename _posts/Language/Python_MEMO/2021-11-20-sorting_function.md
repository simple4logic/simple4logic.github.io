---
title:  "Sorting Function"
search: false
categories: 
  - Python_MEMO
tags:
  - programming
  - function
  - Python
  - method
excerpt: "간편하게 정렬시키자"
---

# 파이썬의 sorting 함수
___

## 개념
sort 함수는 말 그대로 정렬을 위한 함수이다. 리스트 정렬은 물론 문자도 정렬이 가능하다.

## 예시

리스트 정렬 시에
```py
listA = [5, 2, 4, 3, 1]  
sorted(listA)
>>> [1, 2, 3, 4, 5]
```

문자도 문제 없이 정렬 가능하다(리턴값 = 리스트)
```py
stringB = 'zbdaf'  
sorted(stringB)
>>> ['a', 'b', 'd', 'f', 'z']
```

위에서 stringB의 결과를 다시 결합하고 싶으면 .join을 쓸 수 있다.  
```py
"".join(sorted(stringB))
#참고 : join 에서 "X" 결합 사이에 X를 삽입
>>> abdfz
```

리스트 자료형에서 sort 메소드를 이용하면 리스트 자체를 정렬할 수 있다(제자리 정렬, in-place-sort). 리턴값을 따로 없다.  

- alist.sort() #리스트 자체를 정렬  
- alist = blist.sort() #잘못된 문장  

sorted에서 key= 옵션을 통해 정렬을 위한 기준(or 함수)를 별도 지정 가능하다.  

len을 통해 정렬하는 경우
```py
listC = ['ccc', 'aaaa', 'd', 'bb']  
sorted(c, key=len)
>>> ['d', 'bb', 'ccc', 'aaaa']
#알파벳 순서가 아니라 길이 순으로 정렬했다.
```

함수를 이용해 정렬하는 경우  
```py
listD = ['cde','cfc', 'abc']
sorted(listD, key=lambda s:(s[0], s[-1]))
>>> ['abc', 'cfc', 'cde']
#첫번째 정렬 기준은 s[0]이고 두번째 정렬 기준이 s[-1]
#첫번째 단어 a, c ,c 를 통해 먼저 abc가 앞에 오고, 같은 두 놈은 마지막 단어 c와 e를 통해 cfc가 두번째로 왔다.
```