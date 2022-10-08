---
title: "JSX와 Elements, 리액트로 시계 만들기"
layout: post
tags: React
---

<a href="https://feb-dain.github.io/basic-react/">리액트 기초</a>에서 Component와 props, State는 정리한 적이 있는데
JSX와 Element에 대해서는 정리한 적이 없어 먼저 이론을 확실하게 이해하고 넘어가고자 한다.

### JSX란? 
JavaScript Syntax Extension의 약자로 JavaScript XML이라고도 불린다.
쉽게 말해 JSX는 자바스크립트와 HTML이 결합된 것이라고 할 수 있다. 
브라우저 실행 전, 바벨(Babel)이 JSX로 작성된 코드를 자바스크립트 코드로 변환한다.<br>
`그럼 왜 자바스크립트가 아닌 JSX를 사용하는 것일까?`<br>
리액트에서 자바스크립트 문법 그대로 사용해 HTML을 생성할 경우, 가독성이 좋지 않고 코드가 길어지기 때문에
대부분 JSX를 이용하여 코드를 작성한다.











### Elements란?
Elements are the smallest building blocks of React apps.<br>
<u>리액트 앱에서 가장 작은 구성 요소를 말한다.</u>


Let’s say there is a < div > somewhere in your HTML file:<br>
HTML 파일 어딘가에 < div > 가 있다고 했을 때, <br>

```
<div id="root"></div>
```
  
We call this a "root" DOM node because everything inside it will be managed by React DOM.<br>
이걸 "루트" 돔 노드라고 부른다. 왜냐하면 이 안에 있는 모든 것들이 리액트 돔에 의해 관리될 것이기 때문이다.<br>
<br>
To render a React element, first pass the DOM element to ReactDOM.createRoot(), then pass the React element to root.render():<br>
리액트 엘리먼트를 렌더링하기 위해서는 우선 DOM 엘리먼트를 ReactDOM.createRoot()에 전달한 다음, 리액트 엘리먼트를 root.render()에 전달해야 한다.  

![image](https://user-images.githubusercontent.com/108778921/194708186-15ea11c0-2b64-4486-97e8-7540e47f337c.png)

React elements are immutable. Once you create an element, you can’t change its children or attributes.<br>
리액트 엘리먼트는 불변한다. 엘리먼트를 만들면 엘리먼트의 자식이나 속성을 변경할 수 없다.<br>

-<a href="https://reactjs.org/docs/rendering-elements.html">출처</a><br>

<br>
강의를 듣고 추가적으로 공식 문서를 찾아본 다음, 리액트로 시계를 만드는 연습을 했다.

```jsx
import { useEffect, useState } from "react";

function Clock() {
    const [clock, setClock] = useState(new Date());

    useEffect(()=> {
        const time = setInterval(() => {
            setClock(new Date());
        }, 1000);
        return(() => clearInterval(time));
    }, []);

    return (
        <div>
            <h1>시계</h1>
            <p>{clock.toLocaleTimeString()}</p>
        </div>
    );
}

export default Clock;
```

<br>
자바스크립트에서는 항상 getHours나 getMinutes 등을 사용했는데, 리액트로 시계를 만들면서
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleTimeString">toLocaleTimeString()</a>이
있다는 걸 처음 알았다😂 지금이라도 알게 되어 다행이다.<br>

<br>
