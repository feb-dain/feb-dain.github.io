---
title:  "바닐라 자바스크립트로 그림 앱 만들기"
layout: post
tags: JavaScript
---

운동하다가 허리를 심하게 다쳐서 오늘 코딩을 많이 하진 못했다. 완전히 완성하지 못해서 아쉽지만 부상은 내가 어떻게 할 수 있는 게 아니니까 어쩔 수 없지...😢 
당분간은 잘 쉬면서 틈틈이 코딩하고, 허리가 많이 나아지면 열심히 코딩해야겠다. 그리고 디자인은 누워서도 할 수 있으니까 누워서 그림판 디자인하고 그대로 CSS로 적용해봐야겠다!
작은 프로젝트를 하나씩 만드니까 보람도 있고 재미도 있다. 이렇게 연습하다보면 나중에 내가 원하는 앱도 뚝딱 만들 수 있겠지...? 😂<br>

### 1. 그림판 만들기










```
ctx.lineWidth =  2;
let isPainting = false; 

// 클릭 후, 사용자가 이동할 때마다 그림이 그려지도록 만들기
// ctx.moveTo(e.offsetX, e.offsetY);
function onMove(e){
    if(isPainting){
        ctx.lineTo(e.offsetX, e.offsetY);
        ctx.stroke();
        return;
    }
    ctx.moveTo(e.offsetX, e.offsetY);
}
function onMoveDown(){
    isPainting = true;
}
function cancelPainting(){
    isPainting = false;
}

canvas.addEventListener("mousemove", onMove);
canvas.addEventListener("mousedown", onMoveDown);
canvas.addEventListener("mouseup", cancelPainting);

// click은 마우스를 눌렀다가 뗐을 때 발생
// mousedown은 마우스가 눌러진 상태

//canvas 밖으로 나갔을 때, 다시 누르지 않아도 그려지는 오류 고치기
canvas.addEventListener("mouseleave", cancelPainting);
```

### 1-1. 선의 굵기 바꾸기
```
<canvas></canvas> 
<input id="line-width" type="range" min="1" max="10" value="5" />
```
```
const canvas = document.querySelector("canvas");
const lineWidth = document.getElementById("line-width");

const ctx = canvas.getContext("2d");

canvas.width = 800;
canvas.height = 800;
ctx.lineWidth = lineWidth.value;    // 연결

let isPainting = false;

function cancelPainting(){
    isPainting = false;
    ctx.beginPath();    // 마우스를 움직일 때마다 새로운 path 생성
		// 도중에 선 굵기 변경해도 이전 선에 영향을 안 주기 위함.
}
function lineWidthChange(e){
    ctx.lineWidth = e.target.value;    // 변화를 캐치
}

canvas.addEventListener("mouseup", cancelPainting);

// 선 굵기 조절
lineWidth.addEventListener("change", lineWidthChange)
```
#### 1-1-1. input range 속성 : step
```
<input id="line-width" type="range" min="1" max="10" 
       value="5" step="0.5" />
<!-- step: 단계 변경 `기본 : 1->2... step 0.5 : 1 -> 1.5...` -->
```

### 1-2. 색상 변경
```
<input id="color" type="color" />
```
```
const color = document.getElementById("color");

function colorChange(e){
    ctx.strokeStyle = e.target.value;
    ctx.fillStyle = e.target.value;
}

// 선 색상 변경
color.addEventListener("change", colorChange);
```

### 1-3. 색상 변경 팔레트 제공

HTML
```
<div class="color-option" style="background-color: #cd84f1;" data-color="#cd84f1"></div>
<div class="color-option" style="background-color: #ffb8b8;" data-color="#ffb8b8"></div>
<div class="color-option" style="background-color: #ff3838;" data-color="#ff3838"></div>
<div class="color-option" style="background-color: #ff9f1a;" data-color="#ff9f1a"></div>
<div class="color-option" style="background-color: #fff200;" data-color="#fff200"></div>
<div class="color-option" style="background-color: #32ff7e;" data-color="#32ff7e"></div>
<div class="color-option" style="background-color: #17c0eb;" data-color="#17c0eb"></div>
<div class="color-option" style="background-color: #7158e2;" data-color="#7158e2"></div>
<div class="color-option" style="background-color: #3d3d3d;" data-color="#3d3d3d"></div>
<div class="color-option" style="background-color: #67e6dc;" data-color="#67e6dc"></div>

<!-- 속성 data-"": ""안에 원하는 값(string) 넣을 수 있다.  -->
<!-- 값은 dateset에 나와있다. -->
```
💡 <열 일괄 선택 단축키>
   >맥: cmd + shift + L<br>
   >윈도우: shift + alt + i
   
<br>

CSS
```
/* 팔레트 */
.color-option {
    width: 50px;
    height: 50px;
    cursor: pointer;
}
```

<br>
JS


```
const color = document.getElementById("color");
const colorOptions = Array.from(
    document.querySelectorAll(".color-option")
    // = const colorOptions = document.getElementsByClassName(".color-option");
);

function colorChange(e){
    ctx.strokeStyle = ctx.fillStyle = e.target.value;
}
function colorClick(e){
    const colorValue = e.target.dataset.color; // dataset에 접근해서 미리 설정한 color 추출
    ctx.strokeStyle = ctx.fillStyle = color.value = colorValue;    
    // 클릭한 컬러 color에 동기화
}

// 색상 변경
color.addEventListener("change", colorChange);

colorOptions.forEach((color) => color.addEventListener("click", colorClick));
// 클릭될 때마다 함수 실행
// 함수가 아니라는 오류
// why? colorOptions은 배열이 아니라 HTMLcollection이기 때문에 가져올 수 없어서
// => 배열로 만들어줘야 한다. Array.from();
```

### 1-4. 배경색 채우기, 리셋, 지우개
```
<button id="mode-btn">Fill</button>
<button id="reset">Reset</button>
<button id="eraser">Eraser</button>
```
```
const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");

const modeBtn = document.getElementById("mode-btn");
const reset = document.getElementById("reset");
const eraser = document.getElementById("eraser");

canvas.width = 800;
canvas.height = 800;

const CANVAS_WIDTH = ctx.canvas.width;
const CANVAS_HEIGHT = ctx.canvas.height;

let isFilling = false;

// 채우기 모드(배경색 바꾸기), 그리기 모드
function onMode(){
    if(isFilling){
        isFilling = false;
        modeBtn.innerText = "Fill";
    }else{
        isFilling = true;
        modeBtn.innerText = "Draw";
    }
}
function canvasClick() {
    if(isFilling){
        ctx.fillRect(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);
    }
}

// 리셋
function onReset(){
    // ctx.fillStyle = "white";
    // ctx.fillRect(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);
    ctx.clearRect(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);
}
// 지우개
function onEraser(){
    ctx.strokeStyle = "white";
    isFilling = false;
    modeBtn.innerText = "Fill";
}

modeBtn.addEventListener("click", onMode);
reset.addEventListener("click", onReset);
eraser.addEventListener("click", onEraser);
```

#### 1-4-1. 지우개 색상 (하얀색이 아닌 바탕색으로 바꾸기)
```
let filledColor = "white";

function canvasClick() {
    if(isFilling){
        ctx.fillRect(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);
        filledColor = ctx.fillStyle;
    }
}

function onEraser(){
    ctx.strokeStyle = filledColor;    // 지우개 색상 배경색으로 바꾸기
    isFilling = false;
    modeBtn.innerText = "Fill";
}
```
### 1-5. 이미지 업로드
```
<input type="file" accept="image/*" id="file" />
<!-- accept image 안 하면 비디오도 선택할 수 있음 -->
```
```
const file = document.getElementById("file");

// 이미지 업로드
function fileChange(e){
    const file = e.target.files[0];
    const url = URL.createObjectURL(file);    // 브라우저는 url로 파일을 불러온다. // 다른 브라우저에서는 사용 불가능한 url 
    const img = new Image();
    img.src = url;
    img.onload = function(){
        ctx.drawImage(img, 0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);
        fileInput.value = null;    
        // 사용자가 다른 사진도 선택할 수 있게 사진 업로드하면 선택된 파일 없음이 뜨게 한다.
    }
}

file.addEventListener("change", fileChange);
```

### 1-6. 텍스트 입력
```
<input type="text" placeholder="Write and then double click" id="text" />
```
```
const txtInput = document.getElementById("text");

ctx.lineCap = "round";    // 브러쉬 모양 둥글게

function dbClick(e){
    const txt = txtInput.value;
    if (txt !== ""){
        // ctx.save();    // ctx의 현재 상태(색상, 스타일 등) 저장할 수 있음
        ctx.lineWidth = 1;    // 텍스트 굵기 1으로 변경 -> 브러쉬에도 영향 줌
        ctx.font = "48px sans-serif";
        ctx.fillText(txt, e.offsetX, e.offsetY);
        // ctx.restore();    // save와 restore 사이에서는 어떤 것도 저장되지 않을 것
        ctx.lineWidth = lineWidth.value;
    }
}

canvas.addEventListener("dblclick", dbClick);    // ❗ 오타 주의 "dbl"click임!
```

### 1-7. 이미지 저장
```
<button id="save">Save Image</button>
```
```
const save = document.getElementById("save");

function onSave(){
    const url = canvas.toDataURL();    // 이미지 url 링크로 변환
    const a = document.createElement("a");
    a.href = url;
    a.download = "myDrawing.png"    // 이미지 파일 이름
    a.click();
}

save.addEventListener("click", onSave);
```

<br>
**Code Challenges** 
<br>
+ 텍스트 크기 조절<br>
+ 도형 그리기<br>
+ 채우기 브러쉬<br>
+ CSS 꾸미기<br>

<br>
With <a href="https://nomadcoders.co/javascript-for-beginners-2/lobby">노마드 코더 바닐라 JS로 그림 앱 만들기</a>

<br>
<br>

![image](https://user-images.githubusercontent.com/108778921/191291432-98838a16-23bc-4508-85a7-c84b974444a5.png)

<br>


