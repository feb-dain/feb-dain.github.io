---
title:  "깃허브 블로그 만들고 jekyll 테마 적용하기"
layout: post
---
<br>
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
레파지토리 이름(Repository name)을 원하는 것으로 바꾸면 된다. (변경은 Settings>General>Repository name을 바꾸고 rename을 누르면 된다.) 
보통은 "user name.github.io"로 이름을 설정하는 듯하다.


<br>

## 본격적으로 깃허브 블로그를 만들고 Jekyll 테마 적용해보자!

원하는 jekyll 테마 깃허브로 가서 

![image](https://user-images.githubusercontent.com/108778921/189264526-eecf8a55-46bf-4731-96d0-5e24453ee6fe.png)

Download ZIP를 누르고 파일을 다운받은 다음, 폴더와 파일을 드래그해서 내 레파지토리에 업로드하면 될 것 같지만... 안 된다. 무한 로딩의 늪에 빠지게 된다.
<strong> 따라서 Download ZIP를 누르고 파일을 다운받은 파일을 터미널을 이용해 내 레파지토리에 업로드 해야 한다. </strong>

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

경로 이동  (생략 가능, 어디에 다운로드 하는지만 알고 있으면 된다.)

👇<br>

`git clone 복사한 HTTPS 주소`

