---
title:  "리액트 설치하기"
layout: post
tags: React
---


리액트 설치하기 전에 먼저 Node.js가 설치되어 있어야 한다. <br>
`Node.js를 설치`했다면 다음과 같은 순서로 진행하면 된다. <br>
<br>

### 1. VS code 작업 영역에 폴더 추가  →  폴더 생성 
&nbsp;❗&nbsp; react라는 폴더명은 오동작 할 수 있으니 피할 것
<br>
<br>

### 2. 새 터미널 열기
&nbsp;❗&nbsp; powershell은 오류가 날 수 있으니 cmd나 다른 거 사용하는 걸 추천
<br>
<br>




### 3. 터미널에 “npx create-react-app .” 입력    
<span style="color:gray">_여기서 . (dot)은 현재 폴더에 생성하는 것을 의미한다._</span>
<br>
<br>

### 4. “npm start”를 입력하면 자동으로 웹 브라우저 창이 뜨고, react 코딩할 수 있는 환경이 세팅된다.

>src 폴더 : 내 모든 파일을 넣을 폴더, 가장 중요한 건 “index.js”.<br>
초기 화면은 app.js에서 수정하면 변경 가능<br>
"auto-reload"라서 변경할 때마다 새로고침 안해도 된다.

<br>

### 5. index.js에서 필요한 것 빼고 다 지우기
( 깔끔하게 처음부터 시작하기 위해서다. )

<br>

### 6. App.js에서도 필요한 것 빼고 다 지우기
````
function App() {
  return (
    <div>
      <h1>Welcome back!</h1>
    </div>
  );
}
export default App;
````

### 7. src 폴더 > App.css, App.test.js, index.css, logo.svg, reportWebVitals.js, setupTests.js 파일 지우기

<br>

### 8. propTypes 설치 

#### - 터미널에 “npm i prop-types” 입력
    
❗ 만약 아래와 같은 오류가 발생했다면 <br>
````
To address all issues (including breaking changes), run:

npm audit fix --force

Run `npm audit` for details.
````
<br>
터미널에  yarn 설치하고 prop-types 설치하면 된다!

````
npm install --global yarn

yarn add prop-types
````

<br>
