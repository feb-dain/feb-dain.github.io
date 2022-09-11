---
title:  "깃허브에 리액트 배포하기"
layout: post
tags: React
---

# 깃허브에 React 간단하게 배포하는 방법

### 1. package.json 파일에 코드 2줄 추가

````
"deploy" : "gh-pages -d build",
"predeploy" : "npm run build"
````

![image](https://user-images.githubusercontent.com/108778921/189518749-9bc4d2c8-2f86-4960-b84c-44244ad65eaa.png)
<p> </p>
<p> </p>
<p> </p>

<br>  

### 2. (가독성을 위해) 맨 밑에 homepage 코드 추가

````
  "homepage" : "https://github.com/user-name/repository-name.git"
````

![image](https://user-images.githubusercontent.com/108778921/189518734-85b5215a-2fb3-4d57-be13-13275a672db2.png)

<br>

### 3. 작업 폴더 터미널에 “npm run build” 작성 
<br>

### 4. 해당 폴더에 build 폴더 만들어지면 ❗build 폴더 안❗에 있는 파일 모두 드래그해서 깃허브 레파지토리에 업로드
<br>

### 5. 만약 다음과 같은 오류가 발생했다면?
<a href="https://feb-dain.github.io/error-about-react-01/">Manifest: Line: 1, column: 1, Syntax error | net::ERR_ABORTED 404</a>
