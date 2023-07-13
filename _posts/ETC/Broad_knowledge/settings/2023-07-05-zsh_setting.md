---
title:  "ZSH 테마 설정하기"
search: false
categories: 
  - Broad_knowledge
tags:
  - IDE_Set
    
excerpt: "개발환경 꾸미기"
toc : true
---

## Agnoster 테마 수정

터미널 컬러셋을 수정해도 agnoster에서 >>>> 부분의 색깔은 파란색으로 여전히 고정되어 바뀌지 않는다.  

따라서 이 부분을 수정하고 싶다면 우선 다음과 같은 경로로 들어간다.

```
~/.oh-my-zsh/themes
vi agnoster.zsh-theme
```

이 파일에서, Dir 을 검색하면
```
prompt_dir(){
    prompt_segment blue $CURRENT_FG '%~'
}
```

이 부분에서 blue를 다른 색상으로 수정하면 된다.

여기서 사용 가능한 색상은, 256가지 색상을 인터넷에서 검색해서 코드를 검색해서 넣으면 된다. 

> https://www.ditig.com/256-colors-cheat-sheet  

예를 들어, 이 링크 기준으로 'blue'자리에 39를 치면 DeepSkyBlue1 색상으로 들어간다.


