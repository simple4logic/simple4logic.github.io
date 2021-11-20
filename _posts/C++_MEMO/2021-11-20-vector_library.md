---
title:  "Vector Container에 대해서"
search: false
categories: 
  - C++_MEMO
tags:
  - programming
  - C++
excerpt: "알아두면 쓸모있는 벡터 라이브러리"
---

# Vector Library의 활용
___

## 1. 개념
vector container는 메모리가 자동으로 할당되는 배열이다. STL(standard template library)의 일종인데 STL이 무엇인지는 나중에 다뤄보도록 하겠다. Linked List처럼 맨 뒤쪽에 자료를 삽입하거나 삭제할 수 있는 구조이다.  
그러나 배열 기반인만큼 삽입과 삭제가 빈번하게 일어난다면 비효율적이라고 한다. 

## 2. 사용 방법  
사용하기 위해서는 먼저 &#60;vector&#62; 헤더파일을 추가해야 한다.  
벡터를 만들 때 형식은 "vector&#60;자료형&#62; 변수명"이다. 다른 예시들을 보자.

### 1) vector의 생성자, 연산자
vector&#60;int&#62; v;
- 비어있는 vector v를 생성

vector&#60;int&#62; v(5);
- 기본값(0)으로 초기화 된 5개의 원소를 가지는 vector v를 생성

vector&#60;int&#62; v(5, 2);
- 2로 초기화된 5개의 원소를 가지는 vector v를 생성

vector&#60;int&#62; v2(v1);
- v2는 v1 vector를 복사해서 생성됨


### 2) vector 멤버 함수
vector&#60;int&#62; v; 로 정의되어 있는 상태이다.  
참조 : 해당 데이터를 리턴

v.assign(5, 2);
- 2의 값으로 5개의 원소 할당.

v.at(idx);
- idx번째 원소를 참조
- v[idx] 보다 속도는 느리지만, 범위를 점검하므로 안전함

v[idx];
- idx 번째 원소를 참조
- 범위를 점검하지 않으므로 속도가 v.at(idx)보다 빠름

v.front();
- 첫번째 원소를 참조

v.back();
- 마지막 원소를 참조

v.clear();
- 모든 원소를 제거
- 원소만 제거하고 메모리는 남아있음
- size만 줄어들고 capacity는 그대로 남아있음

v.push_back(7);
- 마지막 원소 뒤에 원소 7을 삽입

v.pop_back();
- 마지막 원소를 제거

v.begin();
- 첫번째 원소를 지정 (iterator와 사용)

v.end();
- 마지막의 "다음"을 지정 (iterator와 사용)

v.rbegin();
- reverse begin을 지정 (거꾸로 해서 첫번째 원소를 지정)
- iterator와 사용.

v.rend();
- reverse end 을 지정 (거꾸로 해서 마지막의 다음을 지정)
- iterator와 사용.

v.reserve(n);
- n개의 원소를 저장할 위치를 예약(미리 동적할당 함)

v.resize(n);
- 크기를 n으로 변경
- 더 커졌을 경우 default값인 0으로 초기화
v.resize(n,3);
- 크기를 n으로 변경
- 더 커졌을 경우 인자의 값을 3으로 초기화

v.size();
- 원소의 갯수를 리턴

v.capacity();
- 할당된 공간의 크기를 리턴
- 공간 할당의 기준은 점점 커지면서로 capacity를 할당함

v2.swap(v1); **이해 잘 안감?
- v1과 v2의 원소와 capacity 바꿈 (모든걸 스왑해줌)
- v1의 capacity를 없앨때 (할당한 메모리를 프로그램이 끝나기 전에 없애고 싶을때) 사용하기도 합니다.
- v2를 capacity가 0인 임시 객체로 만들어서 스왑을 해줍니다.
- vector&#60;int&#62;().swap(v1);

v.insert(2, 3, 4);
- 2번째 위치에 3개의 4값을 삽입 (뒤에 원소들은 뒤로 밀림)

v.insert(2, 3);
- 2번째 위치에 3의 값을 삽입
- 삽입한 곳의 iterator를 반환

v.erase(iter);
- iter 가 가리키는 원소를 제거
- size만 줄어들고 capacity(할당된 메모리)는 그대로 남음
- erase는 파라미터 하나를 받을때와 두개를 받을 때 다름 예제 참고

v.empty()
- vector가 비었으면 리턴 true
- 비어있다의 기준은 size가 0이라는 것이지, capacity와는 상관 없음

### 3) vector의 size와 capacity의 관계
v.size();
- 원소의 갯수를 리턴

v.capacity();
- 할당된 공간의 크기를 리턴
- 공간 할당의 기준은 점점 커지면서로 capacity를 할당하게 됩니다.
- dev c++ 기준으로 string 클래스로 vector 를 만들었을때.
```
원소 수 1 => capacity 1
원소 수 2 => capacity 2
원소 수 3 => capacity 4
원소 수 4 => capacity 4
원소 수 5 => capacity 8
원소 수 6 => capacity 8
원소 수 7 => capacity 8
원소 수 8 => capacity 8
원소 수 9 => capacity 16
```
을 봐서는 2^n으로 capacity의 메모리 할당이 되는 것 같다.  
기존 메모리의 * 2 로 증가하게 된다.  
이런식으로 메모리 할당을 하는 이유는 push_back이 일어날때 마다 동적할당을 하면, 비효율적이기 때문  
원소 개수가 증가하면서, 메모리를 증가해서 따로 할당하게 되면 
기존위치에 메모리를 이어서 할당하는게 아니라 새롭게 메모리를 할당해서 원소들을 전부 복사하는 형태  
기존에는 복사에 대한 비용이 많이 들었었는데 std::move 라는 것이 도입되면서 복사하지 않고 이동하게 되어 메모리 증가에 따른 비용이 많이 들지 않게 되었음.  

*capacity와 size의 핵심적인 차이 *  
- size : 할당된 메모리 안에 요소가 들어있는것의 개수 
- capacity : 할당된 메모리의 크기

<br>

> 출처 : https://blockdmask.tistory.com/70
