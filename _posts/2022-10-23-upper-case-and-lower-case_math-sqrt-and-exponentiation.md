---
title: "대문자 ↔ 소문자, 제곱근 판별"
layout: post
tags: Coding-Test
---

왜... 레벨 0이 레벨 1보다 어렵지...? 안 풀리는 문제는 일단 건너뛰고 풀리는 문제부터 풀었다.

### 대문자와 소문자
문자열 my_string이 매개변수로 주어질 때, 대문자는 소문자로 소문자는 대문자로 변환한 문자열을 return하도록 solution 함수를 완성해주세요.
```jsx
function solution(my_string) {
    return Array.from(my_string,x => x === x.toUpperCase() ? x.toLowerCase() : x.toUpperCase()).join("");
}
```






대문자일 경우 toLowerCase를 이용해 소문자로 만들어 주고 소문자일 경우 toUpperCase로 만들어준 뒤, join으로 합쳐주었다.

```jsx
function solution(my_string) {
    return my_string.split("").map((v, index) => my_string.charCodeAt(index) < 97 ? v.toLowerCase() : v.toUpperCase()).join("");
}
```
어떤 사람은 위와 같이 코드를 작성했다. charCodeAt(index)은 index에 대한 UTF-16 코드를 나타내는 0 ~ 65535 사이의 정수를 반환한다고 한다.
<a href="https://velog.io/@hyejeong/%EB%8C%80%EB%AC%B8%EC%9E%90-%EC%B0%BE%EA%B8%B0">이 블로그</a>에 따르면 유니코드 대문자는 65 ~ 90을,
소문자는 97 ~ 122 값을 갖는다고 한다. 그래서 97 미만이구나! 예상은 했지만, 찾아봄으로써 확실하게 알게 되었다. 😊

<br>

### 정수 제곱근 판별
임의의 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하려 합니다.
n이 양의 정수 x의 제곱이라면 x+1의 제곱을 리턴하고, n이 양의 정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하세요.

```jsx
function solution(n) {
    return Math.sqrt(n) % 1 === 0 ? (Math.sqrt(n)+1)**2 : -1;
}
```
Math.sqrt을 이용해 제곱수를 판별하고(<a href="https://feb-dain.github.io/max-number_median_square-numbers-and-reordering-string/">제곱수 판별에 대한 설명</a>) 
n이 제곱수일 경우, n의 제곱근에 1을 더해 거듭제곱( ** )을 해주었다. 만약 n이 제곱수가 아닐 경우, -1을 반환했다.

<br>
<br>
