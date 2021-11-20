---
title:  "범위 기반 for 루프"
search: false
categories: 
  - Cpp_MEMO
tags:
  - programming
  - C++
excerpt: "python 스타일의 range-based-for-loop"
toc : true
---

# Range Based For loop에 대해서
___

## 개념
일반적으로 우리가 아는 for loop는 다음과 같이 쓰인다.  
> for(int i = 0; i < n ; i ++){}  

이 경우 익숙하지만, 인수도 많고 해서 실수가 나오기 쉽다. 그래서인지 C++ 11버전부터는 파이썬에서 지원하던 Range Based loop를 for을 통해서 구현할 수 있도록 기능이 추가되었다. 직접적인 예시를 통해서 분석해보자. 


## 참고 코드

```cpp
/*BOJ Q19246574의 참고제출*/
#include <vector>
long long sum(std::vector<int> &a) {
	long long ans = 0;
    for (auto v : a) {
      ans += v;
    }
	return ans;
}
```
해당 답안은 아주 간결하고 깔끔하게 쓰였다. 바로 Range Based For loop를 사용했기 때문이다. 이를 뜯어서 분석해보자.

### 0. vector<int> &a
std::vector<int> &a는 sum이라는 함수가 인수로서 int형 vector a를 입력받겠다는 의미이다. 배열을 입력받을 때와 마찬가지로 그냥 vector a가 아닌, a의 주소 &a형태로 입력을 받았다.

### 1. colon 연산자
":" 연산자의 경우 python에서 썼던 range마냥 편리한 연산자이다. A : B(=array or vector)일 경우 A는 B의 모든 요소들을 처음부터 끝까지 대입한다. 아래를 보자. 

```cpp
int main(){
    int fibonacci[] = {0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89};
    for (int number : fibonacci)
        std::cout << number << ' ';
    return 0;
```
이 코드에서는 number이라는 (처음 선언된) int변수에 fibonacci라는 array의 모든 값이 한번씩 대입된다. 처음에는 0, 다음에는 1, ... 이런식으로 array의 끝까지 반복된다. 아주 편리한 method라 볼 수 있다.

### 2. auto
auto의 경우 자동적으로 자료형을 맞추도록 컴파일러에게 지시하는 명령어이다. 위의 참고 제출 코드를 다시 한 번 보자.

```cpp
for (auto v : a) {
      ans += v;
    }
```
이 코드에서 a는 분명 int형 vector이다. 따라서 a라는 vector의 내부 값들은 모두 int이다. v는 vector a에서 iterate할 것이기 때문에 v에 대입될 값들은 int일 것이다. 따라서 auto v는 자연스럽게 int v로 컴파일러가 바꿔주게 된다.

## 추가 내용  
기존에 쓰던 인수를 세개나 먹는 for loop를 쓰려면 일회성 변수들을 선언하는 등 낭비가 꽤 심했다. Range Based For loop를 사용하면 간결하면서도 의도한대로 기능을 잘 실행해주는 코드를 짤 수 있다.