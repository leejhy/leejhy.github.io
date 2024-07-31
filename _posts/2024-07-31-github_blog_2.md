---
title: "깃허브 블로그 시작 가이드 - 2"
date: 2024-07-29 14:21:00 +09:00
categories: [Blog]
tags: ["github", "github blog", "blog", "howto", "가이드", "깃허브 블로그"]
---

> [이전 글](https://leejhy.github.io/posts/github_blog_1/)

## 블로그 설정 변경하기
<br>

먼저 블로그 설정을 변경하려면 루트 디렉토리에 있는 _config.yml 파일을 수정해야 한다.
<img src = "/assets/img/github/2_config.png" alt="config 파일" style="width:80%;">

### _config.yml
위 사진처럼 생긴 파일인데 주석에 설명이 잘 돼있어서 주석만 보고도 설정 할 수 있을것 같지만 감이 잘 안잡힌다 변경 해줘야할 부분들은 아래와 같다.

> `title`: 설정하고 싶은 블로그 이름   
`tagline`: 블로그 이름 밑에 나오는 subtitle 느낌   
`description`: 검색할때 쓰이는 설명들, 본인의 블로그에 맞는 단어들   
`url`: 블로그의 URL  ***(본인 깃허브 닉네임).github.io***   
`github.username`: 본인의 깃허브 닉네임   
`social.name`: 본인의 이름   
`social.email`: 본인 이메일 (아무거나)   
`social.links`: 해당되는 링크 적어주면 된다   

이제 하나씩 어디에 적용 되는건지 살펴 보겠다.

> 헷갈리시면 제 [깃허브](https://github.com/leejhy/leejhy.github.io){:target="_blank"} _config.yml 파일 참고해주세요
{: .prompt-info }

#### 참고사항
다들 아시겠지만 social.name 처럼 중간에 점 `.` 찍어 놓은 부분은 저런 키가 있다는게 아니라, social의 하위 키 name을 의미합니다   
![](/assets/img/github/2_key.png){: width="300px"}*social.name*

<br>
<!-- 2560 1920 1024 768 360 -->
### 적용 부분
아래 사진에서 Leejhy라고 적혀있는 부분이 `title`, 개발 공부정리 라고 적혀있는 부분이 `tagline`이다 저 동그란 프로필 사진은 아바타 사진을 변경하면 된다.   
![](/assets/img/github/2_title.png){: width="300px"}   
<br>

루트 디렉토리에서 /assets/img/avatar.png 위치에 있는 `avatar.png`를 원하는 사진으로 변경하면 된다 나는 옛날에 처음으로 도트로 찍어본 고양이를 넣어봤다 나의 첫 고양이   
![](/assets/img/github/2_avatar.png){: width="300px"}      
<br>
social.name은 이렇게 글을 작성할때 작성자로 표시되고, 페이지 최하단에도 표시된다   
![](/assets/img/github/2_social_name.png){: width="300px"}

--- 

이렇게 블로그 생성부터, 기본 세팅의 가이드는 끝났다!   
다음 글 부터는 글작성 방법과 마크다운 기본 문법, 추가적으로 커스터마이즈 한 부분들등에 대해서 작성해 보겠다
<br><br>
언제나 궁금한점 있으시면 편하게 댓글 달아주세요~ 읽어주셔서 감사합니다