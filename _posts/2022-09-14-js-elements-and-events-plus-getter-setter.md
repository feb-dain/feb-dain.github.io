---
title:  "자바스크립트 요소와 이벤트 이해하기 + 게터, 세터"
layout: post
tags: JavaScript
---

### JavaScript에 있는 Elements(요소)와 Events(이벤트)를 확인하고 싶다면?
MDN 사이트나 개발자 도구에서 많은 요소들과 이벤트들을 확인할 수 있다.

#### 1. MDN

<a href="https://developer.mozilla.org/en-US/docs/Web/API/Element"> Element - Web APIs | MDN </a>

#### 2. console.dir();
```
console.dir(this);
```
<br>













![image](https://user-images.githubusercontent.com/108778921/190188288-fa20e05a-c6f4-425e-ac87-6345a80fb8f6.png)

<br>

### JS로 HTML 호출하는 방법
- **getElementById()**: 해당 아이디 하나만 불러올 수 있다.
- **getElementsByClassName()**: 해당 클래스명으로 불러올 수 있으며, 동일 요소가 있을 시 배열 형태로 불러온다.
- **getElementsByTagName()**: 해당 태그를 불러올 수 있으며, 중복 요소가 있으면 배열 형태로 불러온다.
- **querySelector()/querySelectorAll()**: CSS 형태로 선택할 수 있다 (ex. #id, .class, #id>h1)
  - 중복 요소가 많을 시 querySelector는 첫번째 요소만, querySelectorAll은 해당하는 모든 요소를 배열 형태로 불러올 수 있다.
  - querySelector() : 많이 사용됨

<br>

### Event
- 어떤 행위를 하는 것 (클릭, 호버, wifi 온라인/오프라인 등)
- console.dir()에서 onSomething은 모두 event
- 모든 event는 JS가 listen할 수 있다. 
- eventListener : event를 listen, 하지만 JS에게 무슨 event를 listen하고 싶은 지 알려줘야 함

```
function changeBg(){
  document.body.style.backgroundColor = "tomato";
}
window.addEventListener("resize", changeBg);
```
= "Window에 resize 이벤트가 발생하면 changeBg 함수를 실행시켜줘."<br>
→ JS는 실행함과 동시에 **해당 함수에 첫번째 argument로 object를 넣는다. 이 object에는 event의 정보가 담겨있다.⭐**<br>
⇒ <u>이벤트 정보를 알고 싶다면?</u> <br>
아래와 같이 argument를 받아와서 확인할 수 있다.<br>
```
function onClick(e){
	console.log(e);
	alert("clicked");
}
```
개발자 도구를 확인해보면 이런 식으로 다양한 정보(사용자가 클릭한 위치 좌표, path 등)를 볼 수 있다.

![image](https://user-images.githubusercontent.com/108778921/190352857-bc5c8435-2dc9-4e6a-915d-0d7f01b6a353.png)
![image](https://user-images.githubusercontent.com/108778921/190352868-a6915cbe-a41e-447a-bd23-0c3e8d1f8700.png)

<br>

`<a href="url">`의 default값은 클릭하면 해당 링크로 이동한다는 것이다. 이렇게 이벤트가 가진 default값이 발생하지 않도록 막고 싶다면 ".preventDefault()"를 사용하면 된다.<br>
```
function onLink(e){
    e.preventDefault();
}
```
  
<br>

### JS 실행 과정 (+ getter, setter)

```
<div class="hello">
    <h1 style="color: blue;">Click</h1>
</div>


<script>
    const h1 = document.querySelector("div.hello:first-child h1");

    function titleClick(){
        const currentColor = h1.style.color;    // getter, 색상을 "가져옴"
        let newColor;    // 변수 선언, 상태 : empty
        if (currentColor === "blue"){    // 현재 값 확인
            newColor = "tomato";    // blue라면 tomato로 변경
        }else{
            newColor = "blue";    // blue가 아니라면 blue로 변경
        } // 어떤 색상을 정할지 고민하는 과정
        h1.style.color = newColor; 
        // setter, 정한 색상 값을 "설정". newColor를 h1.style.color에 대입
    }

    h1.addEventListener("click", titleClick);
</script>
```

❗ 설명을 하기 위해 JS에서 style을 바꿨지만, style은 css에서 바꾸는 것이 좋다.
<br>
