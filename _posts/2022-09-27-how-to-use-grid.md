---
title:  "CSS Grid 사용법"
layout: post
tags: CSS
---

![image](https://user-images.githubusercontent.com/108778921/192562365-619aa7ff-2134-40fb-bb1e-bba419d70283.png)

<p> — 열(columns) : grid-template-columns </p>
<p> | 행(rows) : grid-template-rows </p>








```
.container {
	display: grid;     /* 부모에 그리드 선언 */
	grid-template-columns: repeat(5, 1fr);    /* 1:1:1:1:1의 비율 */
	grid-auto-rows: 150px;    /* 열에 맞춰서 150px씩 할당해줘 */
}
```

<br>

### 만약 그리드 박스 안 콘텐츠의 길이가 다양하다면?
grid-auto-... 사용!
```
.container {
	display: grid;
	grid-template-columns: repeat(5, 1fr);
	grid-auto-rows: minmax(150px, auto);
	/* 최소 150px 유지, 콘텐츠가 많을 경우 콘텐츠에 맞춰 늘어난다. */
}
```

```
.container {
	display: grid;
	grid-template-columns: repeat(5, 1fr);
	grid-auto-rows: 150px;
	grid(-column/row)-gap: 1rem;    /* grid cell 사이의 여백 */
  /* column 이나 row, 둘 중 하나만 선택해 여백을 줄 수 있다. */ 
  /* (= padding: 10px;) */ 
}
```

<br>

### 그리드 순서?

![image](https://user-images.githubusercontent.com/108778921/192551749-e067759d-bc6f-4793-b723-77414911bcde.png)

박스를 어디서부터 어디까지 차지하게 할 지 정할 수 있다.

```
.item2 {
	grid-column-start: 2;
	grid-colunm-end: 4;
	grid-row-start: 1;
	grid-row-end: 3;
}
```
```
grid-column: 2/4;
/* (= grid-column: 2 / span 2;) cell 2개를 차지해줘 */
grid-column: 2/-1; /* 끝까지 */
grid-row: 1/3;
```

좀 더 수월하게 하려면 **grid-template-areas**를 사용하면 된다. 
```
.image {
	width: 100%;    /* 부모가 기준 */
	height: 100%;
  object-fit: cover;    /* 사진을 박스 안에 어떻게 들고올 것인지 결정 */
}
```
```
.container {
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-auto-rows: 150px;   
	grid-gap: 1rem; 
	grid-template-areas:
		'a a a'
		'b c c'
		'b c c'
}

.image1 {
	grid-area: a;
}
.image2 {
	grid-area: b;
}
.image3 {
	grid-area: c;
}
```
이렇게 하면 image1은 a영역 만큼 차지, image2는 b영역 만큼, image3는 c영역 만큼 차지 한다.

<br>

### 배운 것을 바탕으로 혼자 사용해보자!

![image](https://user-images.githubusercontent.com/108778921/192558383-c4386468-7988-490e-a2fa-d85294c3372b.png)

```
body {
	width: 100vw;
	height: 100vh;
	margin: 0;
	display: grid;
	grid-template-columns: 3fr 1fr;
	grid-template-rows: 100px auto 50px;
	grid-template-areas:
	  'header header'
	  'main aside'
	  'footer footer';
	text-align: center;
}
header, footer {
	background: black;
  	color: white;
}
header {
	grid-area: header;
}
footer {
	grid-area: footer;
}
main {
	grid-area: main;
}
aside {
	grid-area: aside;
	background: orange;
}
```

With 드림코딩<br>
<a href="https://www.youtube.com/watch?v=nxi1EXmPHRs">CSS Grid 완전 정리 끝판왕 😎</a>

<br>

---

<br>

### Grid 내용 안에 있는 텍스트 수직 가운데 정렬하기

드림코딩 강의를 다 듣고난 뒤, 그리드를 연습하면서 그리드 박스 안에 있는 텍스트를 수직 가운데 정렬을 하고 싶었다. vertical-align: middle;을 사용하면
바로 될 줄 알았는데 텍스트는 전혀 미동도 하지 않았다. 어떻게 하면 수직 가운데 정렬을 할 수 있을까, 구글링을 하던 중 `inline-block 박스`를 만들고
그 박스에다가 `vertical-align: middle;`을 적용하면 된다는 정보를 발견했다. 

```
body {
	width:100vw;
	height: 100vh;
	margin: 0;
	display: grid;
	grid-template-columns: 3fr 1fr;
	grid-template-rows: 100px auto 50px;
	grid-template-areas:
	  'header header'
	  'main aside'
	  'footer footer';
	text-align: center;
}
header, footer {
	background: black;
  color: white;
}
header {
	grid-area: header;
  line-height: 100px;
}
footer {
	grid-area: footer;
  line-height: 50px;
}
.main {
	grid-area: main;
  vertical-align: middle;
}
aside {
	grid-area: aside;
	background: orange;
}
div { 
	display: inline-block;
  height: 100%;
	vertical-align: middle; 
}

<header>Header</header>
<main><div>Main<div></main>
<aside><div>Aside<div></aside>
<footer>Footer</footer>
```

이렇게 했더니 수직 가운데 정렬 성공! 🤗

<br>
