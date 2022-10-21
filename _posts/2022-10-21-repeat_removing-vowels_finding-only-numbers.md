---
title:  "문자 반복, 모음 제거, 숫자만 골라 합하기"
layout: post
tags: Coding-Test
---

### 문자 반복 출력하기
문자열 my_string과 정수 n이 매개변수로 주어질 때, my_string에 들어있는 각 문자를 n만큼 반복한 문자열을 return 하도록 solution 함수를 완성해보세요.

```jsx
function solution(my_string, n) {
    return my_string.split("").map((x)=>x.repeat(n)).join("");
}
```





repeat을 빨리 못 떠올려서 오래 걸렸던 문제...😂 
split으로 문자열을 하나씩 자르고 문자 하나하나를 n 만큼 반복해 준 뒤, join으로 합쳐주었다.

```jsx
function solution(my_string, n) {
    return Array.from(my_string, x=>x.repeat(n)).join("");
}
```
다른 코딩 테스트 문제를 풀면서 ES6 문법인 <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from">Array.from</a>이 기억났는데,
이 문제에서도 일일이 split → map 하는 대신 Array.from을 사용하면 더 깔끔하게 코드를 작성할 수 있겠다는 생각이 들어 적용해봤다. 잘 작동한다!

<br>

### 모음 제거
영어에선 a, e, i, o, u 다섯 가지 알파벳을 모음으로 분류합니다. 문자열 my_string이 매개변수로 주어질 때 모음을 제거한 문자열을 return하도록 solution 함수를 완성해주세요.

```jsx
function solution(my_string) { 
    return my_string.split("").filter((string)=>string !== "u" && string !== "i" && string !== "a" && string !== "e" && string !== "o").join("");
}
```
나는 filter 조건에 and 연산자를 사용해서 코드가 무척 길어졌는데😂, 아래와 같이 includes를 사용하면 간결하게 코드를 작성할 수 있다.
```jsx
function solution(my_string) {
    return Array.from(my_string).filter(string => !["a", "e", "i", "o", "u"].includes(string)).join("");
}
```
```jsx
function solution(my_string) { 
    return my_string.split("").filter(string => !["a", "i", "e", "o", "u"].includes(string)).join("");
}
```
위의 코드는 Array.from을 사용했고, 아래의 코드는 split을 사용했다.

includes는 괄호 안에 있는 문자가 포함되어 있을 경우 true를, 아니면 false를 반환한다.
true, false로만 값을 반환해서 이걸 사용할 생각은 못 했었는데, filter가 true인 값만 반환하는 것을 이용하다니 정말 신기했다.
>추가 설명 : string에 a, i, e, o, u가 포함되어 있으면 true를 반환한다. 하지만 "!(느낌표)"를 이용하여 true의 반대인 false를 반환하게 만든다.
따라서 string에 a, i, e, o, u가 있는 경우, filter에 false가 반환되므로 a, i, e, o, u는 필터에 가로막혀 나올 수 없게 된다.
결과적으로 영어의 모음을 제외한 알파벳(true 값)만 필터를 통과해 나올 수 있는 것이다.)

<br>

### 숨어있는 숫자의 덧셈

```jsx
function solution(my_string) {
    return my_string.split("").filter(Number).map(x=>Number(x)).reduce((a,b) => a+b);
}
```
나는 문자열을 하나씩 잘라낸 배열로 만들고 filter로 숫자만 거른 후,<br>
( 이때 [ "a","A","b","1","B","2","c","C","3","4","o","O","p" ] → [ "1","2","3","4" ] 이런 식으로 걸러진다. )<br>
map으로 문자열을 숫자열로 바꾸고 reduce로 숫자의 합을 구해주었다.

그런데 문제를 풀고 나니 아래와 같이 한 사람들도 있었다.

```jsx
function solution(my_string) {
    return my_string.match(/\d/g).reduce((acc, cur) => acc + Number(cur), 0)
}
```

```jsx
function solution(my_string) {
    return my_string.replace(/[^0-9]/g, '').split('').reduce((a, b) => +b + a, 0);
}
```
/\d/g 이런 거나 /[^0-9]/g 이런 건 처음 보는 것이었다. 그래서 찾아봤다!
- <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions">
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions
</a>

- <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Cheatsheet">
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Cheatsheet
</a>

<br>
Regular Expressions, 한국어로는 정규 표현식이라고 부른다.

>Character classes<br>
Character classes distinguish kinds of characters such as, for example, distinguishing between letters and digits.<br>
Character classes를 사용하면 문자와 숫자를 구분할 수 있는 것처럼 문자/기호 등을 구별할 수 있다.

위에서 사용한 `\d`는 `[0-9]`와 같다. 숫자인 것을 찾아낸다.<br>
Matches any digit (Arabic numeral). Equivalent to [0-9]. For example, /\d/ or /[0-9]/ matches "2" in "B2 is the suite number".

`[^0-9]`는 `\D`와 같다. 숫자가 아닌 것을 찾아낸다.<br>
Matches any character that is not a digit (Arabic numeral). Equivalent to [^0-9]. For example, /\D/ or /[^0-9]/ matches "B" in "B2 is the suite number".

`g`는 global이다.<br> 
Global search로 모든 문자를 검색한다. g를 쓰지 않으면 첫 문자만 검색된다. `[^0-9]`의 예시처럼 "B2 is the suite number"에서 첫 문자인 "B"만 나온다.

```jsx
function solution(my_string) {
    return my_string.match(/\d/g).reduce((acc, cur) => acc + Number(cur), 0)
}
```
따라서 이 코드는 문자열에서 숫자만 찾아내 reduce로 숫자의 합을 구한 것이고

```jsx
function solution(my_string) {
    return my_string.replace(/[^0-9]/g, '').split('').reduce((a, b) => +b + a, 0);
}
```
이 코드는 숫자가 아닌 것을 공백으로('') 바꾸고 split으로 하나씩 잘라 배열을 만든 후, reduce로 그 배열 안에 있는 각 숫자의 합을 구한 것이다.<br>
아래의 코드보다는 위의 코드가 간결하고 좋은 것 같다.<br>
<br>

정규 표현식 ^^... 신세계다. 잘 사용하면 정말 편할 듯하다.

<br>
<br>
