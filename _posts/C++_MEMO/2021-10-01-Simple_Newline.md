---
title:  "빠른 개행"
search: false
categories: 
  - C++_MEMO
tags:
  - programming
  - I/O
  - C++
excerpt: "puts()"
toc : true
---

# 빠른 개행의 방법
___

## 개념
puts() 함수 : c언어에서 쓰이는 함수로 printf함수와는 다르게 기본적으로 개행을 해준다.

따라서, puts("");를 해주면 printf("\n"); 처럼 귀찮게 개행을 하지 않아도 된다.

```cpp
puts("");    
printf("\n");
//둘은 완전히 동일하다.
```

여담으로, endl;는 개행하는 동시에 flush하기 때문에 훨씬 더 많은 연산이 필요하다. 따라서 사용을 최대한 삼가하는 것이 좋다.