---
title:  "리액트 기초"
layout: post
tags: React
---

### Why react?
왜 리액트를 사용해야 하는가?<br>

: JavaScript는 다른 부분도 업데이트되는 반면, React는 html 코드에서 “변하는 부분만” 업데이트된다.<br>
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

### props? 
Properties의 준말, 부모 컴포넌트에서 자식 컴포넌트로 값을 전달할 때 사용한다. (읽기 전용) 

<br>
