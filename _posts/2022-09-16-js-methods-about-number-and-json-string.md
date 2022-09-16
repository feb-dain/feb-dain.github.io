---
title:  "number와 JSON string 관련 메서드"
layout: post
tags: JavaScript
---

## 여러 number 메서드 중에 자주 사용되는 2가지 메서드

### parseInt
string → number로 바꿔준다.

### isNaN : is not a number?
number인지 아닌지 확인할 수 있다.
- boolean, 즉 true or false 값으로 알려준다.
- number ❌ : true
- number ⭕ : false











```
const age = parseInt(prompt("How old are you?"));

      if (isNaN(age) || age < 0){
          alert("Please write a real positive number.");
      }else if(age < 18){
          document.write("You're so young.");
      }else if(age >= 18 && age <= 50 ){
          document.write("You can drink!");
      }else if(age > 50 && age <= 80){
          document.write("You should work out.")
      }else if(age === 100){
          document.write("Wow, are you 100?")
      }else if(age > 80){
          document.write("You can do whatever you want.")
      }
```

✨ 더 다양한 number 관련 메서드는 <a href="https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number">여기서</a>
확인할 수 있다. (<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number">한국어 번역</a>)

<br>

✨ string 관련 자바스크립트 메서드는 <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String">여기서</a>
확인할 수 있다. (<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String">한국어 번역</a>)

<br>

## JSON string 
왜 사용하는가?<br>
<u> 네트워크를 통해 자바스크립트 object를 보내고 싶을 때, 전송 전에 그걸 JSON 문자열로 변환시켜야 하기 때문이다. </u><br>
<br>

### JSON.stringify(변수명)
object, array, 어떤 자바스크립트 코드든 간에 “string”으로 보여준다.

### JSON.parse()
string을 배열로 만든다.<br>
<br>


