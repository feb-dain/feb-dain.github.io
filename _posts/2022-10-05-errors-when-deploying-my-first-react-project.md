---
title: "리액트로 만든 첫 개인 프로젝트를 배포하면서 마주한 문제들"
layout: post
tags: Error
---

혼자 리액트 개인 프로젝트를 하면서 마주한 문제들 중에 가장 힘들었던 건 깃허브 배포였다. 
예전에 리액트 연습하고 깃허브 배포를 쉽게 한 적이 있어서<a href="https://feb-dain.github.io/how-to-publish-react/">(링크-깃허브에 리액트 배포하기)</a>
배포는 전혀 걱정하지 않았는데 이게 웬일.
배포 후 내가 마주한 것은 까만 화면뿐이었다…😢 뭐가 문젠가 싶어 구글링을 해봐도 마땅한 해결책이 안 나왔다.
하지만 명확하게 알게 된 것은 오류의 원인. 1) 리액트 폴더 재사용과 2) 리액트 라우터의 문제였다. 









build 파일을 만들어서 깃허브 리포지토리에 붙여 넣는 방식으로 배포하는 건 불가능하다고 보고 깃(터미널)으로 배포를 했는데, 
예전에 연습했던 페이지가 나와서 당황스러웠다. 새로운 폴더가 아닌 예전에 리액트 연습을 했던 폴더에서 그대로 작업을 해 그런 것 같았다. 
그래서 새로운 리액트 폴더를 만들고 파일을 붙여넣기 했다. 그리고 필요한 라이브러리를 설치했다.
  1. 부트스트랩 설치
    ```
    npm i react-icons --save
    ```
  2. Slick 설치
    ```
    npm i react-slick slick-carousel
    ```
  3. <a href="https://feb-dain.github.io/how-to-make-a-carousel-in-react/"> Swiper 설치 </a>
  4. React Router 설치
    ```
    npm i react-router-dom
    ```

분명 그대로 했는데 오류 발생😂 아놔...<br><br>

“실수로 npm을 업데이트했는데 가끔 오류가 뜰 때가 있다. 이럴 때 모듈을 내가 지정한 값으로 바꾸고 모두 재설치 하는 것이 속이 시원할 때가 있다.
`package-lock.json`, `node_modules` 둘을 삭제하고 npm install을 실행해주면 된다.” -<a href="https://xn--os5ba3q.com/m/67"> 출처 </a>
<br>
<br>
혹시나 해서 위의 방식을 시도해봤는데... 그래도 안 됐다. 오류 메시지를 보니 Swiper 문제인 듯했다. 분명 그대로 붙여넣기 했는데 폴더를 바꾸니 안되는 상황… 구글링으로 열심히 해결 방법을 찾아봤다. 

1. 다운그레이드 (낮은 버전 설치) `npm i swiper@6.8.4`
2. CSS 파일 변경
```jsx
// import "swiper/css"; 
// import "swiper/css/navigation";
👇
import 'swiper/swiper.min.css';
```

참고<br>

[Module not found: Can't resolve 'swiper/react'](https://stackoverflow.com/questions/69202975/module-not-found-cant-resolve-swiper-react)

[[Solved] Module not found: Can't resolve 'swiper/css'](https://namespaceit.com/blog/module-not-found-cant-resolve-swipercss)

<br>
둘 다 하고 기존 CSS 파일 코드를 지우니 해결 😅휴... 해결한 방법으로 블로그 글도 수정했다. 👉 <a href="https://feb-dain.github.io/how-to-make-a-carousel-in-react/">(링크)</a><br>
이제 로컬 페이지에서는 잘 보이게 되었다. 하지만...! 깃허브 배포를 하면 역시나 까만 화면만 보였다. 이를 해결하기 위해 아래와 같은 시도를 했다.<br>


#### 1. 유저 네임 = 깃허브 아이디랑 동일하게 만들기

```
git config --gloabal user.name 바꿀-이름
```

#### 2. gh-pages (재)설치

```
npm i gh-pages
```

#### 3. remote 연동 url 변경 (git remote -v 하면 기존의 url 확인 가능)

```
git remote set-url origin https://github.com/github-user-name/repository-name/
```

#### 4. package.json > homepage 부분 주소 변경

```
"homepage": "https://github-user-name.github.io/repository-name/"
```

#### 5. 라우터에 basename 추가 (path에도 하면 안 먹힘)

```jsx
<BrowserRouter basename={process.env.PUBLIC_URL} id="root">
    <Routes>
        <Route path="/" element={<Home />} />
    </Routes>
</BrowserRouter>
```

<br>

( 오류 고치면서 출처랑 해결 방법을 노션에 틈틈이 기록했는데 거의 다 날아갔다…😄… 노션… 앞으로 중요한 내용은 다른 곳에 적어야겠다.
지금은 기억에 의존해서 적는 중이라 빠진 부분이 있을 수 있다. )

<br>

겨우겨우 배포 성공했으나… 또!! 문제 발생. public > img 폴더에 있는 이미지가 안 뜬다…😢 이것도 역시나 경로의 문제일 거라 확신했다.
'라우터에 url 추가한 것처럼 이미지 파일 앞에도 추가해 볼까?'라는 생각이 들어 시도해 봤는데 오류 해결 성공!  

```jsx
<img src={`${process.env.PUBLIC_URL}/img/logo.png`} alt="로고"></img>
```

다행히 금방 해결됐다…😂

배포 때문에 몇 시간 동안 컴퓨터 앞에서 붙박이가 됐었다… <br>
다사다난 했지만 문제를 모두 해결한 덕에 이제 수정하자마자 터미널에 npm run deploy만 적으면 자동으로 깃허브에 배포된다. 너무 편리하다!
<br>
<br>
