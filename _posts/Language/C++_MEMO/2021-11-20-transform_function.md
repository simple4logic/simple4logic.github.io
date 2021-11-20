---
title:  "Transform Function"
search: false
categories: 
  - Cpp_MEMO
tags:
  - programming
  - C++
excerpt: "값을 손쉽게 변경해보자"
toc : true
---

# transform function 에 대해서
___

## 1. 개념  
transform 함수는 &#60;algorithm&#62;에 정의되어 있다.  
특정 함수를 써서 값을 변경시킬 때 유용하다.  
넣을 input A를 함수 f에 통과시켜서 output B를 뽑아내고 싶을 때 편하다.  

Array의 경우 각 값을 다 바꾸기 위해선 iterate한 방식으로 loop를 돌려야하는데 이 경우 코드가 난잡해진다. input 형식은 array도 단일 값도 모두 가능하다.

## 2. 형태  

### 1) 단항 함수형
넣을 함수의 parameter가 하나인 경우  
ex) int add(int n) 이면 single parameter 이다.  
이때 함수는

```cpp
template <class InputIt, class OutputIt, class UnaryOperation>
OutputIt transform(InputIt first1, InputIt last1, OutputIt d_first,
UnaryOperation unary_op);
```

- first1, last1 : transform 함수를 적용할 원소들을 가리키는 범위  
- d_first : 결과를 저장할 범위 (first1과 동일해도 된다. 이 경우, 기존 데이터를 덮어쓴다)
- unary_op : 원소들을 변환할 함수

> first1부터 last1 전까지 범위의 원소들을 unary_op를 수행하고, 그 결과를 d_first부터 차례로 저장한다

### 2) 이항 함수형
넣을 함수의 paramter가 두 개인 경우
ex) int cmp(int a, int b) 이면 double parameter 이다.  

```cpp
template <class InputIt1, class InputIt2, class OutputIt, class BinaryOperation>
OutputIt transform(InputIt1 first1, InputIt1 last1, InputIt2 first2,
OutputIt d_first, BinaryOperation binary_op);
```
단항일때랑 거의 유사한데, InputIt2 first2가 추가되었고 template에서 input1이랑 2랑 나뉜다. parameter도 모두 동일하며
- first2 : transform 함수를 적용할 두 번째 원소들의 시작점  

만 추가되었다.  

> first1부터 last1 전까지 범위의 원소들과 first2부터 동일 갯수의 원소들로 binary_op를 수행하고, 그 결과를 d_first부터 차례로 저장한다

## 3. 사용 예시  

```cpp
int twice(int n) {
    return n*2;
} //binary_op
 
int main(){
	
std::vector<int> vec = {1, 2, 3, 4, 5};
 
    for(int i = 0; i < vec.size(); i++){
    std::cout << vec[i];
    } //before transform 출력
    std::cout << std::endl;
 
    std::transform(vec.begin(), vec.end(), vec.begin(), twice);
 
    for(int i = 0; i < vec.size(); i++){
    std::cout << vec[i];
    } //after transform 출력
    return 0;
}
// 실행 결과
 
1, 2, 3, 4, 5
1, 4, 9, 16, 25
```  


## 4. 사용 case  
letter과 같은 string 형태의 배열에서 모두 소문자/대문자로 변경을 해야할 때 transform 함수를 적용하면 편하게 바꿀 수 있다.  

> 출처 : https://artist-developer.tistory.com/28