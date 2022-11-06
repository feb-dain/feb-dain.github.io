---
title: "우테코 프리코스 2주차를 하면서"
layout: post
tags: JavaScript
---

promise는 콜백(callback) 지옥에 빠지지 않게 도와주는 유용한 자바스크립트 object이다. (=코드를 간결하게 작성할 수 있도록 도와준다.)
미래의 어떤 시점에 결과를 제공하겠다는 '약속'을 한다.
promise를 사용하면 state(상태)는 잠시 대기(pending)되었다가 성공하면 fulfilled, 실패하면 rejected로 바뀐다.

![image](https://user-images.githubusercontent.com/108778921/200172096-6547e3a0-41bf-4fd9-a4d7-a361abb6eb73.png)

```jsx
const promiseA = new Promise((resolutionFunc, rejectionFunc) => {
  resolutionFunc(777);
});
// At this point, "promiseA" is already settled.
promiseA.then((val) => console.log("asynchronous logging has val:", val));
console.log("immediate logging");

// produces output in this order:
// immediate logging
// asynchronous logging has val: 777
```

숫자 야구 게임을 순수 자바스크립트(바닐라 자바스크립트)로 풀 수 있으려면
callback, promise, async/await 등의 개념을 잘 알고 있어야 할 것 같아 문제 푸는 것을 멈추고 강의를 듣기 시작했다.

<a href="https://www.youtube.com/watch?v=s1vpVCrT8f4"> 드림코딩 강의 </a>

위의 드림코딩 강의를 들으면서 공부했는데, 잘 설명해주셔서 이해가 잘 되었다. 
하지만 이해가 잘 되는 것과 적용을 잘 하는 것은 별개의 문제이기에 😂 이해한 개념을 가지고 숫자 야구 게임을 만들어 보려고 한다.
만약 HTML을 사용할 수 있었다면 이미 완성했을텐데... 자바스크립트로 만드는 건 정말 어렵다.

하지만 그 덕분에 자바스크립트의 다양한 기능들을 공부할 수 있었다.
then은 들어봤지만 catch, finally, try 등은 처음 들어보는 것들이었다.
콜백 지옥에 빠질 수 있는 코드를 간단하게 만들어주는 소중한 기능들...

### try...catch
실행할 코드블럭을 표시하고 예외가 발생(throw)할 경우의 응답을 지정한다.

```jsx
try {
  nonExistentFunction();
} catch (error) {
  console.error(error);
  // expected output: ReferenceError: nonExistentFunction is not defined
  // Note - error messages will vary depending on browser
}
```
catch를 이용해 오류가 발생했을 때 어떤 것을 실행시킬지 정할 수 있다.

```jsx
try {
  try_statements
}
[catch (exception_var) {
  catch_statements
}]
[finally {
  finally_statements
}]
```
finally는 try 선언이 끝난 뒤, 예외 발생 여부와 상관없이 실행된다.

**new Promise에 전달되는 함수를 executor(실행자, 실행 함수)라고 부르는데, executor는 new Promise가 만들어질 때 자동으로 실행되므로
불필요한 입력값이 생길 수 있다. 이를 주의하며 사용할 것!**

<br>
<br>
