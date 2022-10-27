---
title: "가장 큰 수 찾기, 중앙값, 제곱수, 문자열 정렬"
layout: post
tags: Coding-Test
---

### 가장 큰 수 찾기

```jsx
function solution(array) {
    const max = Math.max(...array);
    return [max, array.indexOf(max)];
}
```
Math.max로 가장 큰 수를 찾고, indexOf로 인덱스 번호를 찾았다. 










<br>

### 중앙값 구하기

```jsx
function solution(array) {
    array.sort((x, y) => x-y);
    return array.at(Math.floor(array.length/2));
}
```
sort로 배열을 오름차순으로 정렬하고, at으로 원하는 인덱스 번호에 있는 것을 반환했다. 

```jsx
function solution(array) {
  return array.sort((a, b) => a - b)[Math.floor(array.length / 2)];
}
```
array[n]으로도 원하는 인덱스 번호에 있는 것을 반환할 수 있다는 것을 잠시 잊었다 😂

<br>

### 제곱수 판별하기
어떤 자연수를 제곱했을 때 나오는 정수를 제곱수라고 합니다. 정수 n이 매개변수로 주어질 때, n이 제곱수라면 1을 아니라면 2를 return하도록 solution 함수를 완성해주세요.

```jsx
function solution(n) {
    return Math.sqrt(n) % 1 === 0 ? 1 : 2;
}
```
sqrt을 이용해 n의 제곱근을 구한 뒤, 제곱근이 소수점을 가질 경우 2를, 소수점을 가지지 않을 경우(=n이 제곱수일 경우) 1을 반환하도록 했다.
`number % 1`을 하면 소수점 이하의 값만 구할 수 있다.

```jsx
function solution(n) {
    return Math.sqrt(n) === Math.floor(Math.sqrt(n)) ? 1 : 2
}
```
이런 식으로 한 사람도 봤다! 소수점 자리가 없을 경우, 버림하더라도 n의 제곱근과 같은 수일 테지만, 소수점 자리가 있을 경우, 같은 수가 아닐 것이다.  

<br>

### 문자열 정렬하기 (2)
영어 대소문자로 이루어진 문자열 my_string이 매개변수로 주어질 때, my_string을 모두 소문자로 바꾸고 알파벳 순서대로 정렬한 문자열을 return 하도록 solution 함수를 완성해보세요.

```jsx
function solution(my_string) {
    return [...my_string.toLowerCase()].sort().join("");
}
```
문자 하나 하나가 나뉘어진 배열로 만들고, 알파벳 순서대로 정렬한 다음, 다시 하나의 문자로 합쳤다.

```jsx
function solution(my_string) {
    return my_string.toLowerCase().split('').sort().join('');
}
```
문자열 정렬하기 (1)에서는 위의 코드처럼 split을 이용했는데 다시 할 땐 깜빡했다. 😂 문자열 정렬할 때는 `split → sort → join` 이 순서를 기억하자!


출처: 프로그래머스 코딩 테스트 연습, https://school.programmers.co.kr/learn/challenges
<br>
<br>
