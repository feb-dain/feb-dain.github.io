---
title: "하샤드 수(각 자릿수의 합), 문자 → 정수, 중복 문자 제거"
layout: post
tags: Coding-Test
---

### 하샤드 수 (Harshad number)
양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다.
예를 들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다. 
자연수 x를 입력받아 x가 하샤드 수인지 아닌지 검사하는 함수, solution을 완성해주세요.







```jsx
function solution(x) {
    let sum = String(x).split("").reduce((acc, cur)=> acc+Number(cur),0);
    return !(x%sum);
}
```
자릿수의 합을 먼저 구했다. x를 문자형으로 바꾸고 split으로 하나씩 자른 뒤, 다시 정수로 만들어 총합을 구해주었다.
> ex) 18 -String→ "18" -split→ [ "1", "8" ] -reduce+Number→ [ 1, 8 ] → 1+8 = 9
<br>

어떤 사람은 아래와 같이 코드를 작성했다.
```jsx
function Harshad(n){
  return !(n % (n + "").split("").reduce((a, b) => +b + +a ));
}
```
옛날 코드라 지금은 이대로 실행하면 런타임 에러가 난다.
그래서 다음과 같이 바꿔주었다.
```jsx
function solution(x) {
    let sum = (x+"").split("").reduce((acc, cur)=> +cur + +acc);
    return !(x%sum);
}
```
잘 작동된다!
근데 이 코드를 보다가 문득 의문이 생겼다. `String(x)` 과 `x+""`중 어느 것이 좋은 코드일까? 
실행 속도는 `x+""` 이게 더 빠른데... string이 더 직관적이니 좋은 걸까...? 흠... 이 정도는 상관없나? 알아봐야겠다. 🤔

<br>

### 문자열을 정수로 바꾸기
문자열 s를 숫자로 변환한 결과를 반환하는 함수, solution을 완성하세요.

제한 조건
- s의 길이는 1 이상 5이하입니다.
- s의 맨앞에는 부호(+, -)가 올 수 있습니다.
- s는 부호와 숫자로만 이루어져있습니다.
- s는 "0"으로 시작하지 않습니다.

```jsx
function solution(s) {
    return Number(s);
}
```
보자마자 푼 문제! 쉽게 풀린 것도 좋았지만, 다른 사람들의 코드를 보는 것도 정말 흥미로웠다.

```jsx
function strToInt(str){ 
    return str/1 
}
```
```jsx
function strToInt(str){ 
    return +str;
}
```
`문자형과 숫자형의 사칙연산은 숫자형`이 나온다는 것을 이용한 코드이다.
이렇게 풀 수도 있다니! 신기했다.

<br>

### 중복된 문자 제거
문자열 my_string이 매개변수로 주어집니다. my_string에서 중복된 문자를 제거하고 하나의 문자만 남긴 문자열을 return하도록 solution 함수를 완성해주세요.

```jsx
function solution(my_string) {
    return Array.from(new Set(my_string)).join("");
}
```
`Array.from`과 `set`을 이용해 풀었다. set은 중복된 배열을 없애준다.

```jsx
function solution(my_string) { 
    return [...new Set(my_string)].join(''); 
}
```
`...(dots)`와 `set`을 이용해 푼 사람도 있었다. 코드 속도는 위의 코드가 더 빠른데 아래의 코드가 간결하니까 더 좋은 코드인 걸까? 
'좋은 코드란 무엇인가'에 대한 궁금증이 계속 생긴다. 아무래도 클린 코딩에 관한 책이나 글을 많이 읽어야 할 것 같다! 🤓

<br>
<br>
