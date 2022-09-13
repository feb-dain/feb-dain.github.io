---
title:  "리액트 기초"
layout: post
tags: React
---

### Why react?
왜 리액트를 사용해야 하는가?<br>

JavaScript는 다른 부분도 업데이트되는 반면, React는 html 코드에서 “변하는 부분만” 업데이트된다.<br>
⇒ `인터렉티브에 최적화`<br>
게다가 `코드가 간결하고, 유지보수가 쉽다.`

<br>






### Component?
컴포넌트 : 함수(function), 객체(object)
- 컴포넌트 이름은 항상 대문자로 시작해야 한다.
- UI를 `재사용 가능한 개별적인 여러 조각`으로 나누고, 각 조각을 개별적으로 나누어 코딩한다.<br>
 
이 <a href="https://goddaehee.tistory.com/299?category=395445">블로그</a>에 자세하게 설명되어 있다.

<details>
<summary>💡 컴포넌트 팁 💡</summary>
<div markdown="2">
  &nbsp;&nbsp;무작정 잘게 자른다고 좋은 게 아니다. "재사용성"을 고려해 나눠야 한다. <br>
  &nbsp;&nbsp;<b>정확한 이유가 없다면 미리 분리하지 말고, 필요할 때 적절하게 분리하는 것이 좋다</b>
</div>
</details>
<br>

### props? 
Properties의 준말, 부모 컴포넌트에서 자식 컴포넌트로 값을 전달할 때 사용한다. (읽기 전용) 

<br>

### State?
Basically where your data will be, 기본적으로 데이터가 저장되는 곳이다.<br>
- state가 변하면 계속 render된다.
- 컴포넌트에서 동적인 값을 state라고 부르는데, `useState` 즉 state를 사용하여 값을 변경할 수 있다. 

````
const [state, setState] = useState(initialState);
const [데이터, 데이터변경함수] = useState(초깃값(생략 가능));
````

````
import {useState} from "react";

function App() {
  const [counter, setValue] = useState(0);
  const onClick = () => setValue((prev) => prev + 1);
  return (
    <div>
      <h1>{counter}</h1>
      <button>Click me</button>
    </div>
  );
}

export default App;
````

<br>

### useEffect?
If you want some code in your components only to run the first time and never again, then you should useEffect.<br>
state가 변할 때마다 렌더링되지 않고, 딱 한 번만 실행됐으면 좋겠다면 "useEffect"를 사용하면 된다.<br>

❗  첫 render할 때 console에 코드가 두 번 찍힐 경우, `index.js파일 안 React.StrictMode를 지우면 된다.`
<br>

````
import {useEffect} from "react";

useEffect(() => {
    console.log("Call the api");
  }, []);
````
Watch "[ ]"라고 말하는 것과 같다. 위의 경우, 리액트가 볼 것이 없기 때문에 딱 한 번만 실행된다.
<br>
<br>

````
useEffect(() => {
    console.log("Search for", keyword);
  }, [keyword]);
````
React에게 “Watch keyword”라고 말하는 것과 같다. keyword가 바뀔 때만 실행된다.<br>
<br>

만약 첫 렌더딩 때, Search for가 안 떴으면 좋겠다면 조건문을 이용하면 된다. 

````
useEffect(() => {
    if(keyword !== ""){
      console.log("Search for", keyword);
    }
  }, [keyword]);
````

and 연산자를 이용해 조건을 여러 개로 설정할 수도 있다.

````
useEffect(() => {
    if(keyword !== "" && keyword.length > 5){
      console.log("Search for", keyword);
    }
  }, [keyword]);
````

"[]"안에 여러 개를 넣을 수도 있다.

````
useEffect(() => {
    console.log("I run when 'counter' changes.");
  }, [counter]);
  useEffect(() => {
    console.log("I run when keyword & counter change.");
  }, [keyword, counter])
  ````
<br>
<br>

### useEffect와 useState 활용
````
import {useEffect, useState} from "react";

function Hello(){
  useEffect(() => {
    console.log("hi:)");
    return () => console.log("bye :(");
  }, []);
  return <h1>Hello</h1>;
}

function App() {
  const [showing, setShowing] = useState(false);
  const onClick = () => setShowing((prev) => !prev);
  return (
    <div>
      {showing ? <Hello /> : null }
      <button onClick={onClick}>{showing ? "Hide" : "Show"}</button>
    </div>  
  );
}

export default App;
````
<br>

### Clean-up : component가 사라질 때 뭔가 할 수 있도록 해주는 것
````
function Hello(){
  useEffect(() => {
    console.log("created :)");
    // Clean up function
    return () => console.log("destroyed :(");
  }, []);
  return <h1>Hello</h1>;
}
````

<br>

### CSS 적용
전체 적용을 원한다면 .css 파일 만들어서 index.js에 import 해주면 된다. (global css)
````
import "./styles.css";
````

하지만 만약 모듈화를 하고 싶다면?<br>
1) Name.module.css 파일을 만들어서
````
.btn {
    color:white;
    background-color: tomato;
}
````

2) 원하는 .js 파일에 import 하고,
````
import styles from "./Button.module.css"
````

3) 적용 원하는 태그에 className을 넣어주면 된다.
````
function Button({text}){
    return <button className={styles.btn}>{text}</button>;
}
````
_Random class name 적용되기 때문에 같은 class name 설정해도 된다._

<br>
