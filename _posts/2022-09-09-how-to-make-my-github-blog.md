---
title:  "깃허브 블로그 만들고 jekyll 테마 적용하기"
layout: post
tags: GitHub-Blog
---
<br>

## 0. 사건의 발단

깃허브 블로그를 만들었는데 글을 작성해도(커밋을 해도) 잔디가 심어지지 않는 문제 발생. 
잔디 심는 재미로 깃허브 블로그를 시작한 것도 있어서 원인과 문제 해결 방법을 찾으려고 열심히 검색을 했다.
user.email이 일치하지 않거나 user.name이 일치하지 않으면 이런 문제가 발생할 수 있다고 한다. 하지만 나의 원인은 이게 아니었다.
<strong> jekyll 테마 깃허브에서 Fork를 눌러 그냥 복사해왔기 때문이었다. </strong> Fork한 레파지토리는 아무리 커밋해도 잔디가 심어지지 않는다고...

<br>

![image](https://user-images.githubusercontent.com/108778921/189262551-8ae4ebba-cc8d-4f3a-9350-e19577a426db.png)
<br>

>❗ [번외] 잔디와 상관없이 편하게 깃허브 블로그를 사용하고, jekyll 테마를 사용하려면
원하는 jekyll 테마의 깃허브로 가서 Fork를 눌러 내 레파지토리에 들고온 뒤, 
레파지토리 이름(Repository name)을 원하는 것으로 바꾸면 된다. (변경은 Settings>General에서 Repository name을 바꾸고 rename을 누르면 된다.) 
보통은 "username.github.io"로 이름을 설정하는 듯하다.


<br>

## 본격적으로 깃허브 블로그를 만들고 Jekyll 테마 적용해보자!
jekyll 테마 사이트 : <a href="https://jekyllthemes.io/free"> https://jekyllthemes.io/free </a> <br>
➕ <a href="http://jekyllthemes.org/">http://jekyllthemes.org/</a> 여기서 테마를 고르면 깃허브로 이동하지 않아도 바로 ZIP 파일을 다운받을 수 있다.<br>
<br>
원하는 jekyll 테마의 깃허브로 가서 

![image](https://user-images.githubusercontent.com/108778921/189264526-eecf8a55-46bf-4731-96d0-5e24453ee6fe.png)

Download ZIP를 누르고 파일을 다운받은 다음, 폴더와 파일을 드래그해서 내 레파지토리에 업로드하면 될 것 같지만... 안 된다. 무한 로딩의 늪에 빠지게 된다.
<strong> 따라서 Download ZIP를 누르고 파일을 다운받은 파일을 터미널을 이용해 내 레파지토리에 업로드 해야 한다. </strong>
<br>
<br>

### 1. 새로운 레파지토리(Repository)를 만든다. - New 버튼 클릭

![image](https://user-images.githubusercontent.com/108778921/189265424-9960da14-deff-4e8f-af32-bbb6e351b0d5.png)

<br>

### 2. Repository 이름을 " username.github.io " 으로 만든다.

> <b> Owner &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Repository name</b> <br>
> Username &nbsp; / &nbsp; username.github.io
<br>

그리고
<br>

![image](https://user-images.githubusercontent.com/108778921/189265989-13e2b6e7-f60e-4546-872f-661542d9500c.png)

Public, Add a README file 선택하고 생성!

<br>

### 3. 내 레파지토리 HTTPS 복사하기

![image](https://user-images.githubusercontent.com/108778921/189267549-77d62e8a-c64a-4067-955c-590317581ae9.png)

<br>

### 4. 터미널을 열고 복사한 레파지토리 폴더를 만들고 싶은 경로로 이동
>Windows : Windows 키 + R -> cmd 검색<br>
>Mac : Command(⌘) + F로 'terminal'을 검색<br>

👇<br>

터미널에서 원하는 경로로 이동
````
cd 폴더명 (다운 받고 싶은 위치)
````
(생략 가능, 단! 어디에 다운로드 하는지만 알고 있으면 된다.)

👇<br>

````
git clone 복사한 HTTPS 주소
````

<br>

### 5. 폴더(username.github.io) 열고 확인차 파일 생성하기

![image](https://user-images.githubusercontent.com/108778921/189270243-521a2b5c-fbfa-4684-9100-ace94003e586.png)

아직은 README 파일만 있는데, 여기에 확인차 파일을 하나 만들어보자.

````
cd username.github.io
echo "GitHub Blog" > index.html
````

![image](https://user-images.githubusercontent.com/108778921/189270622-4f78e0fe-4dac-45b9-a8b4-67d81b276377.png)

짠! index.html 파일 하나가 성공적으로 생성됐다! 그럼 잘 연결된 것이다 👏

<br>

### 6. 내 깃허브 레파지토리에 PUSH

````
git add --all
git commit -m "initial commit"
git push -u origin main
````
⛔ <b>! [rejected] main -> main (fetch first) error: failed to push some refs to</b> 에러가 발생한 경우, 
```
git push -u origin main --force
```
강제로 실행시키면 된다.
<br>
<br>
<b>결과</b>

![image](https://user-images.githubusercontent.com/108778921/189271262-170826b4-f5de-47c7-854c-4b90b0a865cb.png)

성공적으로 연결됐으면 내 레파지토리에 index.html 파일도 생성된 것을 확인할 수 있다.<br>
이제 "username.github.io"을 주소창에 치면? "GitHub Blog" 글자가 나타난다.

<br>

### 7. Ruby 다운로드 (for Windows)
<a href="https://rubyinstaller.org/downloads/" target="_blank"> https://rubyinstaller.org/downloads/ <a>

![image](https://user-images.githubusercontent.com/108778921/189272898-7b0fb8d8-b32c-423f-8d7e-e99ae7e8867e.png)

두꺼운 글씨로 표시된 ' Ruby+Devkit 3.1.2-1 (x64) ' 선택해서 다운로드.<br>
Next를 계속 누르다보면 다운로드 완료. 다운로드가 완료됐다는 것을 알리는 CMD 창이 뜨면 닫기(x) 버튼을 누르면 된다.

터미널에
````
ruby -v
````
입력하면 다운로드한 ruby 버전을 확인할 수 있다.
<br>
<br>

### 8. Jekyll 설치
````
gem install jekyll bundler
````

설치가 완료되면 아까 만든 폴더(username.github.io)에 들어가서 README 파일과 index.html 파일 모두 지워준다.
그리고 터미널에서 위의 폴더로 경로를 바꿔준다.
````
cd username.github.io
````
그러면 이런 식으로 경로가 바뀐다.<br>
<b> ~/username.github.io> </b>
<br>
<br>
여기에 <strong> jekyll new ./ </strong> 입력.

````
username.github.io>jekyll new ./
````

⛔ 아까 폴더 안에 .git 폴더를 제외한 README 파일과 index.html 파일을 지우지 않았다면 오류가 뜨니 <strong>폴더 안의 파일을 모두 지워야 한다!</strong>
<br>
<br>

### 9. bundle 설치
````
bundle install
bundle exec jekyll serve --trace
````
⛔ <b>Webrick LoadError</b> 에러가 발생하면
````
bundle add webrick
````
⛔ <b>Could not find gem 'webric x64-mingw32'</b> 에러가 발생하면
````
gem install webrick
````
<br>
오류 없이 성공적으로 진행되어 Server address: http://127.0.0.1:4000/ 가 뜨면<br>
주소창에 http://127.0.0.1:4000/를 입력해보자.<br>
기본 jekyll 페이지가 뜬다. 파란 글자로 <span style="color:skyblue">Welcome to Jekyll!</span>이 뜰 것.
<br>
<br>

### 10. 내 깃허브 레파지토리에 PUSH
````
git add .
git commit -m "commit!(커밋 메시지: 원하는 메시지로 설정할 수 있음)"
git push
````
![image](https://user-images.githubusercontent.com/108778921/189280302-ad6e0325-3f54-4bc9-b39c-6ac7012d8213.png)
커밋 메시지는 여기에 이렇게 뜬다.
<br>
<br>

### 11. 맨 처음 다운 받은 Jekyll 테마 적용
맨 처음에 다운 받은 jekyll 테마 알집(ZIP) 파일을 풀고, 안에 있는 폴더와 파일을 username.github.io 폴더에 복사 또는 이동시켜준다.
같은 이름을 가진 파일이 이미 있다고 경고창이 뜰텐데 그냥 덮어쓰기하면 된다.

````
bundle install
bundle exec jekyll serve --trace
````
⛔ <b>오류(Webrick LoadError)</b> 발생하면
````
bundle add webrick
````
<br>

### 12. 내 깃허브 레파지토리에 PUSH

````
git add --all
git commit -m "commit!(원하는 커밋 메시지)"
git push 
````
⛔ <b>Conflict: The following destination is shared by multiple files. The written file may end up with unexpected contents.</b> 오류 발생했을 경우, 
index. html 파일(내가 다운받은 jekyll 테마 파일)과 index.markdown 파일(기본 jekyll 파일)이 같이 있어서 그렇다.<br>
필요 없는 <b>index.markdown 파일을 삭제</b>해주면 해결된다.<br>
<br>


# 끝! 👏👏
<br>
<br>  
