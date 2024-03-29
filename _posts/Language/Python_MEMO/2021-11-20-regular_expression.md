---
title:  "Regular Expression"
search: false
categories: 
  - Python_MEMO
tags:
  - programming
  - I/O
  - Python
excerpt: "특정 문자의 선별적 표현"
---

# python 정규 표현식에 대해
___

 > 참고 : https://wikidocs.net/4308

정규 표현식(Regular Expression 혹은 Regexpr or Regex)은 특정한 규칙을 가진 문자열의 집합을 표현하는데 사용하는 언어이다.

## 정규 표헌식에 쓰이는 메타문자
메타 문자란 원래 그 문자가  가진 뜻이 아닌 특별한 용도로 사용하는 문자를 말한다. 
> . ^ $ * + ? { } [ ] \ | ( )

## 문자 클래스 []
1. 문자 클래스로 만들어진 정규식은 "[ ] 사이의 문자들과 매치"라는 의미를 갖는다. 정규 표현식이 [abc]라면 a, b, c 중 하나의 문자와 매치하면 된다는 것.  

    세 문자열 'ab', 'before', 'break'가 있다고 하면 각각 ab, b, ba 가 매치한다.


2. [ ] 안의 두 문자 사이에 하이픈(-)을 사용하면 두 문자 사이의 범위(From - To)를 의미한다. 예를 들어 [a-c]라는 정규 표현식은 [abc]와 동일하고 [0-5]는 [012345]와 동일하다.  

    - [a-zA-Z] : 알파벳 모두  
    - [0-9] : 숫자

3. 문자 클래스 안에 ^ 메타 문자를 사용할 경우에는 반대(not)라는 의미를 갖는다. 예를 들어 [^0-9]라는 정규 표현식은 숫자가 아닌 문자만 매치된다.

## 자주 사용하는 문자 클래스
- \d - 숫자와 매치, [0-9]와 동일한 표현식이다.
- \D - 숫자가 아닌 것과 매치, [^0-9]와 동일한 표현식이다.
- \s - whitespace 문자와 매치, [ \t\n\r\f\v]와 동일한 표현식이다. 맨 앞의 빈 칸은 공백문자(space)를 의미한다.
- \S - whitespace 문자가 아닌 것과 매치, [^ \t\n\r\f\v]와 동일한 표현식이다.
- \w - 문자+숫자(alphanumeric)와 매치, [a-zA-Z0-9_]와 동일한 표현식이다.
- \W - 문자+숫자(alphanumeric)가 아닌 문자와 매치, [^a-zA-Z0-9_]와 동일한 표현식이다.

## 그 외의 정규식들
맨 위의 링크를 참고하자.

## 정규 표현식 치환 메서드 re.sub
문자열을 정규 표현식에 의거하여 치환해주는 메서드로 re.sub가 있다.  
형식은 다음과 같다. 
```
re.sub (정규 표현식, 치환 문자, 대상 문자열)
```

## 예시
```py
s = s.lower()
s = re.sub('[^a-z0-9]', '', s)
```
s라는 문자열을 대상으로, 해당 문자열에서 a부터z 와 숫자 0부터9를 '제외'한('^'이 있기 때문)문자들을 null('')로 치환해준다. 이를 통해서 소문자와 숫자를 제외한 문자들을 모두 삭제할 수 있다.