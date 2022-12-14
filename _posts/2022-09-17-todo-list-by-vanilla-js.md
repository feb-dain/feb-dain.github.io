---
title:  "바닐라 자바스크립트로 Todo list 만들기"
layout: post
tags: JavaScript
---

<a href="https://nomadcoders.co/javascript-for-beginners/lectures/1705">노마드코더 강의</a>를 보면서 같이 To-do list를 만들었고, 이를 만들면서 자바스크립트를 더 잘 이해할 수 있었다!<br>

---

<br>

### 🤔 새로고침해도 생성한 할 일들이 그대로 남아있었으면 좋겠어
프론트엔드 단에서도 값을 기억하는 방법이 있다. 바로 `localStorage`를 이용하면 된다. 
key와 value만 준비하면 로컬스토리지에서도 값을 저장할 수 있다.
로컬스토리지를 이용한 다양한 메서드는 <a href="https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage">여기서</a> 확인할 수 있다.










```
const loginForm = document.querySelector("#login-form");
const loginInput = document.querySelector("#login-form input");
const greeting = document.querySelector("#greeting");
const HIDDEN = "hidden"; 
const USERNAME_KEY = "username";
// 중요한 정보가 아닌 단순 실수 방지를 위해 const 사용하는 경우 변수명 대문자로


function onSubmit(e) {
    // console.log(loginInput.value);
    e.preventDefault();     // 기본 동작 막음 // form을 submit해도 새로고침 안하도록 막음
    loginForm.classList.add(HIDDEN);
    const username = loginInput.value;
    localStorage.setItem(USERNAME_KEY, username);     // 로컬에 저장 
    // setItem("key", "value") // greeting.innerText = "Hello " + username;
    
    // greeting.innerText = `Hello ${username}`;     // 클린 코딩 `String ${변수명}`
    // greeting.classList.remove(HIDDEN);
    groupGreeting(username);
    
}

function groupGreeting(username){
    greeting.innerText = `Hello ${username}`; 
    greeting.classList.remove(HIDDEN);
}

// username이 있는지 없는지 확인
const savedUsername = localStorage.getItem(USERNAME_KEY);

if (savedUsername === null ){
    //show the form
    loginForm.classList.remove(HIDDEN);
    loginForm.addEventListener("submit", onSubmit);
}else{
    //hide the form
    groupGreeting(savedUsername);
}

// console.log(savedUsername); //로컬에 저장된 username value
```

argument를 이용해서 new value 와 saved value를 따로 둔다.
if 이후는 new value가 아닌 저장된 로컬 네임이 있는지 없는지 확인하는 것이기 때문에 saved value를 이용해야 한다.<br>
🤗 왜 다른 argument를 이용하나 했는데 이렇게 생각하니 이해가 됐다.

<details>
<summary>아래의 경우 argument 사용할 필요없지만 localStorage를 두 번 열어봐야 한다.</summary>
<div markdown="1">

```
const loginForm = document.querySelector("#login-form");
const loginInput = document.querySelector("#login-form input");
const greeting = document.querySelector("#greeting");
const HIDDEN = "hidden"; 
const USERNAME_KEY = "username";
// 중요한 정보가 아닌 단순 실수 방지를 위해 const 사용하는 경우 변수명 대문자로


function onSubmit(e) {
    // console.log(loginInput.value);
    e.preventDefault();
    loginForm.classList.add(HIDDEN);
    localStorage.setItem(USERNAME_KEY, username); 
    // greeting.innerText = `Hello ${username}`; 
    groupGreeting();
    
}

function groupGreeting(){
    const username = localStorage.getItem(USERNAME_KEY);
    greeting.innerText = `Hello ${username}`; 
    greeting.classList.remove(HIDDEN);
}

	
const savedUsername = localStorage.getItem(USERNAME_KEY);
   
if (savedUsername === null ){
    //show the form
    loginForm.classList.remove(HIDDEN);
    loginForm.addEventListener("submit", onSubmit);
}else{
    //hide the form
    groupGreeting();
}
```

</div>
</details>
<br>

**forEach**<br>
Array에 있는 각각의 item을 사용할 수 있게 해준다.
submit 이벤트 리스너가 event object를 기본으로 제공해주는 것처럼 JS도 item object를 기본으로 제공해준다.
```
function sayHello(item){
    // console.log("hello", item); // hello item[0~]
}

// 저장되어 있는 Todo 가져오기
const savedTodos = localStorage.getItem(TODOS_KEY);

if(savedTodos !== null){
    const parsedTodos = JSON.parse(savedTodos);
    parsedTodos.forEach(sayHello);
}
```

화살표 함수 (더 간단하게 함수를 실행할 수 있다)
```
parsedTodos.forEach((item) => console.log(object));
```
🤗 각각의 item을 => 이 함수로 실행

```
parsedTodos.forEach(showTodo);
```
“각각의 item을 showTodo 함수로 실행시켜줘!”<br>
🤗 여기서 showTodo 함수는 브라우저에 todo list를 보여주는 함수 ⇒ 저장된 각각의 item을 브라우저에 todo list로 보여준다.<br>

`이전 것(로컬에 저장된 것)과 새로운 것(새로 입력하는 할 일)을 모두 저장하고 싶다.`<br>
→ 먼저 로컬에 저장된 것이 사라지는 이유를 알아보자: todos = [] 비어있는 배열이기 때문에 계속 없어지는 것!<br> 
→ 그러면 비어있는 배열이 아닌 저장된 배열에 새로 추가하면 되겠다!
```
let todos = [];

if(savedTodos !== null){
    const parsedTodos = JSON.parse(savedTodos);
    // 저장된 배열이 존재하면 저장된 배열 + 새로운 배열 추가 해줘
    todos = parsedTodos;
    parsedTodos.forEach(showTodo);
}
```

<br>

### 🤔 이제 Todo list에 삭제 기능을 만들어보자
기존에는 사용자가 할 일을 입력하면 그대로 텍스트로 받았다. 하지만 이러면 컴퓨터가 어떤 할 일을 삭제해야 할지를 모른다.
```
function todoSubmit(e){
    e.preventDefault();
    const newTodo = todoInput.value;
    todoInput.value = "";
    todos.push(newTodo);    // 새로운 todo 저장
    showTodo(newTodo);    // 사용자에게 받은 value 텍스트
    saveTodos();
}
```

👇<br>

**Date.now()** 를 이용하면 난수를 얻을 수 있다.
```
const newTodoOb = {
    text: newTodo,
    id: Date.now(),
};
todos.push(newTodoOb);
```

**새로운 todo를** 텍스트가 아닌 **object로 저장**
```
function todoSubmit(e){
    e.preventDefault();
    const newTodo = todoInput.value;
    todoInput.value = "";
    const newTodoOb = {
        text: newTodo,
        id: Date.now(),
    };
    todos.push(newTodoOb);    // 새로운 todo 저장
    showTodo(newTodoOb);     // 사용자에게 받은 value 텍스트
    saveTodos();
}
```

왜 object로 만들고, 난수를 얻으려고 하는 건가?<br>
🤗 랜덤한 id값을 만들어, 일치하는 id값을 가진 할 일(todo)만 삭제하기 위함이다.<br>

**배열.filter(변수명)** <br>
forEach와 비슷하다.

```
function filterEx(item){
	return item !== 3 
	// item이 3이 아니면 return true! // [1,2,4,5]
	// item이 3일 경우 return false, 따라서 3인 item은 사라진다.
	// 다시 말해, 3이 아닌 모든 item은 필터에 통과되는 것.
}
[1, 2, 3, 4, 5].filter(filterEx) 
// array의 item을 유지하고 싶으면 true 리턴해야 함.

----- 
// 자세한 예시

filterEx(1) = 1
filterEx(2) = 2
filterEx(3) = 3    // 만약 여기서 false가 발생하면 3을 제외한 filterEx(1,2,4)만 실행
filterEx(4) = 4
```
JS는 배열의 각 item을 해당 함수의 첫번째 argument로 전달한다.
⇒ argument는 배열의 각 item이 된다.

<br>

완성한 Todo list를 CSS로 꾸미고, 넣고 싶은 기능들을 혼자서 추가로 더 넣어봐야겠다! 🧐
<br>
