---
title:  "Scanf 함수와 buffer"
search: false
categories: 
  - C++_MEMO
tags:
  - programming
  - I/O
  - C++
excerpt: "입출력에서 buffer 구조"
toc : true
---

# Scanf 함수와 buffer
___

## 문제 상황

scanf 함수는 한줄짜리 행버퍼로 큐구조이다...  
다시 말해 먼저 들어온 값이 먼저 사용된다는 것.  
예를 들어, 2와 3을 입력하고 enter을 눌렀다면 버퍼에는  
2 / 3 / enter(='\n') 가 저장되어 있는 셈이다.
```cpp
scanf("%d %d", &a, &b);
printf("your input : %d %d\n", a, b);
scanf("%c", &c);
printf("in ascii : %d\n", c);
```
이 상황을 보자. 2, 3을 입력하고 A를 입력하려 해도 이미 입력이 마감되어 "in ascii : " 옆에 이상한 dummy 값이 뜬다. 이는 enter가 %c(format specifier)상에서 char로 인식되어 들어가버렸기 때문이다. 

## 해결안
1. %c와 같은 format specifier 앞에 공백을 삽입한다. " %c"처럼 입력하면, %c로 입력된 문자 하나를 무시하게 된다. 이렇게 하면 마지막으로 입력버퍼에 남아있던 enter가 무시된다.

2. fflush(stdin)을 사용한다. 위 코드에서 첫번째 scanf 이후에 한번 flush해서 enter가 들어있는 buffer를 한 번 비워주면 된다.

3. gets 함수를 쓴다. gets 함수는 마지막 enter 키를 null로 바꾸어 저장한다. scanf에서는 %s형식 지정자가 문장 끝에서 알아서 null을 삽입해준다.

## 종합
여태 내가 테스트를 진행한 방식은 linux 시스템 상에서 ./ < in.txt로 입력하던 상황이라 맨 끝에 enter가 들어가 있지 않은 경우가 대부분이다. 하지만 백준에서는 (https://www.acmicpc.net/board/view/62746)에 따르면 test case 입력의 맨 끝에는 일반적으로 \n 개행문자가 들어가 있는 경우가 대부분이다. 따라서 오류가 발생하는 것. 이를 고려해 주어야만 한다.

## 참고 링크
1. https://k-story.tistory.com/223  
2. https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=zlatmgpdjtiq&logNo=221577996732
3. https://www.geeksforgeeks.org/effect-of-adding-whitespace-in-the-scanf-function-in-c/