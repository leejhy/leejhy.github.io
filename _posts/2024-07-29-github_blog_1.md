---
title: "깃허브 블로그 만들기 - 1"
date: 2024-07-29 14:21:00 +09:00
categories: [Blog]
tags: ["github", "github blog", "blog", "howto", "깃허브 블로그"]
---

### chirpy 테마, Mac, iterm2 사용 기준으로 작성하였다.

깃허브 블로그는 github의 무료 호스팅을 이용하기 때문에 먼저 레포리토리를 만들어야 한다.[^1]
## **Github Pages 세팅**

### 1.Repository 생성
github.com 메인화면 좌측에 있는 <kbd>New</kbd> 버튼을 누른 뒤 
<img src = "assets/img/github/1_new_repo.png" style="width:60%;">

아래처럼 입력해준다. 
<img src = "assets/img/github/1_create_repo.png" style="width:80%">
- `Repository name` : (본인의 깃허브닉네임).github.io
- `Public` : 선택
- `Add a README file` : 선택

### 2. 패키지 설치
chirpy 테마가 jekyll에서 지원하는 테마이기 때문에 루비를 설치해야 한다.   
iterm2를 켜서 ruby를 설치한다. 나는 brew를 사용했다.

```zsh
$ brew install ruby
$ echo 'export GEM_HOME=$HOME/gems' >> ~/.zshrc
$ echo 'export PATH=$HOME/gems/bin:$PATH' >> ~/.zshrc
$ source ~/.zshrc
```
루비 설치 이후에 루비 패키지매니저인 gem 을 사용해서 jekyll과 bundler를 설치해준다

```zsh
$ cd ~ #home으로 이동
$ gem install jekyll bundler
```

### 3. 테마 다운로드
테마를 설정할때 fork 받은 뒤 설정하는 방법, zip파일을 받아서 설정하는 방법이 있다고 하는데   
fork는 안 해봤고, zip파일은 init이 안돼서 [여기](https://github.com/cotes2020/jekyll-theme-chirpy.git){:target="_blank"} 에서 clone을 받았다.
```zsh
$ git clone https://github.com/cotes2020/jekyll-theme-chirpy.git theme #테마를 theme 이름으로 clone
$ cd theme #theme 디렉토리로 이동
$ bash tools/init.sh #init 실행
$ rm -rf .git #.git 디렉토리 복사 방지
```
테마를 clone 받은 뒤에 해당 디렉토리에 들어가서 tools/init.sh 파일을 실행하고   
로컬 레포지토리와 깃이 꼬이지 않게 .git 디렉토리를 삭제해준다.
```zsh
$ bash tools/init.sh #init 실행
$ rm -rf .git #.git 디렉토리 복사 방지
```
init 이후에 내 로컬 레포지토리로 모든 파일을 복사해준다.
```zsh
$ cd ~
$ git clone git@github.com:leejhy/leejhy.github.io.git mygit #내 레포지토리 를 mygit 이름으로 clone
$ cd mygit
$ cp -r ~/theme/{.,}* . #숨김파일 포함한 모든 파일을 내 디렉토리로 복사
```
여기까지 기본 테마설치는 끝났다. 테스트 해보려면 로컬 레포지토리 에서
```zsh
$ cd ~/mygit
$ bundle exec jekyll serve
```
명령어를 실행 시킨 뒤 http://127.0.0.1:4000/ 에 접속해보면 된다. 나이스~
실행할때 발생하는 경고메세지는 [뒤에서](http://127.0.0.1:4000/posts/github_blog_1/#%ED%8A%B8%EB%9F%AC%EB%B8%94-%EC%8A%88%ED%8C%85) 해결 하겠다
### 4. Github Pages 테스트
마지막으로 내 깃 레포지토리에 push하면, 자동으로 github action이 실행돼서 호스팅이 된다.
```zsh
$ git add .; git commit -m "test"; git push
```
웹 브라우저에서 (본인의 깃허브닉네임).github.io URL로 접속해보면 된다!

### **트러블 슈팅**
#### **1. division error**   
division error가 발생해서 sass-migrator를 사용해야 된다는 [글](https://sass-lang.com/documentation/breaking-changes/slash-div/)을봐서
```zsh
$ npm install -g sass-migrator
$ sass-migrator division **/*.scss
```
위처럼 했더니 sass-migrator가 에러가 발생했다...   
모든 .scss에 적용을 하는게 아니라 ~/gems/gems에 들어가서 _sass디렉토리 안에있는 scss 파일에만 sass-migrator 를 적용해야 하는 것이었다    
그래서 gems/gems 폴더에 들어가서 _sass 폴더만 이하에만 적용되게 경로를 추가해서 실행해줬다
```zsh
$ cd ~/gems/gems
$ sass-migrator division /_sass/**/.scss
```
해결완료
#### **2. css warning**   
<img src = "assets/img/github/1_bundle_error.png" style="width:80%;">

이 에러는 이 문법이 다음 버전에서 지원하지 않는다는 경고문이라고 한다. 사실 안해도 상관 없을 것 같다 터미널 에러 메세지의 경로 중 가장 위의 경로로 들어가서 표시된 줄을 &{ } 으로 감싸주면된다
```css
margin-left: 20px; /* 이 부분을 */

& {
margin-left: 20px; /* 이렇게 바꿔주면 된다 */
}
```

--- 
이제 기본 설치는 끝났으니, 다음에는 테마를 커스터마이즈 해보겠다.   
혹시나 따라하시다가 궁금한점이나 안되는 부분 있으시면 댓글 남겨주세요!   

---
**참고 자료**

[^1]:[Github Pages](https://docs.github.com/ko/pages/quickstart){:target="_blank"}

