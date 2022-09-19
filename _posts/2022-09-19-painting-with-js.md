---
title:  "자바스크립트로 그림 그리기"
layout: post
tags: JavaScript
---

### 1. 우선 HTML 파일에 canvas 태그를 만든다.
```
<canvas></canvas>
```

### 2. ( CSS로 그림판을 생성한다. ) 생략 가능
```
canvas {
    width: 800px;
    height: 800px;
    border: 1px solid #000;
}

body {
    display: flex;
    justify-content: center;
    align-items: center;
}
```









### 3. 자바스크립트로 선을 긋거나 면을 그린다.
#### 3-1. 연습 (네모 여러 개 만들기)
```
const canvas = document.querySelector("canvas");

const ctx = canvas.getContext("2d");    // 3d도 그릴 수 있다.
canvas.width = 800;
canvas.height = 800;

// ctx.fillRect(50, 50, 100, 200)    // 단축 함수 // x축, y축, width, height
ctx.rect(50, 50, 100, 100);    // 단순한 선 (처음엔 안 보임) // rect도 역시 단축 함수(단축키)다.
ctx.rect(150, 150, 100, 100); 
ctx.rect(250, 250, 100, 100);
ctx.fill();    // 채우기

ctx.beginPath();    // 경로 끊기
ctx.rect(350, 350, 100, 100);
ctx.rect(450, 450, 100, 100);
ctx.fillStyle = "red";    // 경로를 끊어주지 않으면 이 전에 그렸던 것들도 전부 red가 된다. why? 경로(path: ctx)가 같이 때문
setTimeout(() => {
    ctx.fill();
}, 3000);

// 과정(process) 중요하다.
```

#### 3-2. 연습 (선과 면 그리기)
```
const ctx = canvas.getContext("2d");
canvas.width = 800;
canvas.height = 800;

ctx.moveTo(50, 50);    // x, y (시작점)
// 선 그리기 (이동하면서)
ctx.lineTo(150, 50);    // x, y 
ctx.lineTo(150, 150);    // x, y 
ctx.lineTo(50, 150);    // x, y 
ctx.lineTo(50, 50);    // x, y 
ctx.stroke()    // 선
ctx.fill();    // 면
```

#### 3-3. 연습 (집 그리기)
```
ctx.fillRect(200, 200, 50, 200);
ctx.fillRect(400, 200, 50, 200);
ctx.lineWidth = 2;  // 순서 중요하다. strokeRect 밑에 두면 적용 안 됨
ctx.fillRect(300, 300, 50, 100);
ctx.fillRect(200, 200, 200, 20);
ctx.moveTo(200, 200);
ctx.lineTo(325, 100);    
ctx.lineTo(450, 200);    
ctx.fill();
```

#### 3-4. 연습 (사람 그리기)

![image](https://user-images.githubusercontent.com/108778921/191044813-47ecf8c2-ec7e-4378-a72c-8d4dcc9e7353.png)

<span style="color:green"> center </span>: arc(100, 75, 50, 0 * Math.PI, 1.5 * Math.PI)<br>
<span style="color:red"> start angle </span>: arc(100, 75, 50, 0, 1.5 * Math.PI)<br>
<span style="color:blue"> end angle </span>: arc(100, 75, 50, 0 * Math.PI, 1.5 * Math.PI)<br>
circle : arc(100, 75, 50, 0, 2 * Math.PI)<br><br>

```
ctx.fillRect(210 - 40, 200 - 50, 15, 100);
ctx.fillRect(350 - 40, 200 - 50, 15, 100);
ctx.fillRect(220, 150, 60, 200);
ctx.fillRect(180, 150, 60, 10);
ctx.fillRect(260, 150, 60, 10);

ctx.arc(250, 100, 50, 0, 2 * Math.PI)    // x, y, starting angle, ending engle // argument 많다.
ctx.fill();

ctx.beginPath();
ctx.fillStyle = "white";
ctx.arc(260 + 10, 80, 8, 1 * Math.PI, 2 * Math.PI);
ctx.arc(220 + 10, 80, 8, 1 * Math.PI, 2 * Math.PI);
ctx.arc(250, 100, 1, 0.5 * Math.PI, 2 * Math.PI);
ctx.fill();

ctx.beginPath();
ctx.fillStyle = "black";
ctx.fillRect (220, 350, 20, 200);
ctx.fillRect (260, 350, 20, 200);
```

결과물 👇

![image](https://user-images.githubusercontent.com/108778921/191045868-01262aa9-ab8b-4a6a-8795-9394d7af0c37.png)
<p>ㅎㅎㅎ 귀엽다</p>

#### 3-5. 연습 (마우스 이동으로 선 그리기)
```
ctx.lineWidth = 2;
// ctx.moveTo(0, 0); 
// (0.0)에서 시작, 한 번 클릭해도 바로 그림그릴 수 있음.
// 만약 (0.0)에서 시작 안 하려면 moveTo 없이 클릭 두 번하면 된다.

const colors = [
    "#cd84f1",
    "#ffb8b8",
    "#ff3838",
    "#ff9f1a",
    "#fff200",
    "#32ff7e",
    "#17c0eb",
    "#7158e2",
    "#3d3d3d",
    "#67e6dc",
];

function onClick(e){
    e.preventDefalut;
    ctx.beginPath();
    ctx.moveTo(0, 0);
    const color = colors[Math.floor(Math.random() * colors.length)];
    ctx.strokeStyle = color;
    ctx.lineTo(e.offsetX, e.offsetY);    // event object의 좌표
    ctx.stroke();
}
// canvas.addEventListener("click", onClick); // 클릭하면 선이 생김
canvas.addEventListener("mousemove", onClick); // 움직이면 선이 생김
```

원리를 이해해야 하고 위의 과정들이 익숙해져야 한다. ⇒ 많이 연습하기!! 💪<br>

With <a href="https://nomadcoders.co/javascript-for-beginners-2/lectures/1710">노마드 코더 바닐라 JS로 그림판 만들기</a>
<br>
<br>
