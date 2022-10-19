---
title: "각 자릿수의 합, 가장 큰 수와 그 다음으로 큰 수 찾기, 특정 문자 제거"
layout: post
tags: Coding-Test
---

### 자릿수 더하기
자연수 N이 주어지면, N의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.
예를들어 N = 123이면 1 + 2 + 3 = 6을 return 하면 됩니다.

```jsx
function solution(n){
    const numbers = n.toString().split("").map(x => Number(x));
        return numbers.reduce((x, y) => x + y);  
}
```
나는 먼저 toString으로 n을 문자열로 만들고 하나씩 자른 다음, 다시 숫자열로 바꾸고 각 자릿수를 더해주었다.

```jsx
function solution(n){
    return (n+"").split("").reduce((acc, curr) => acc + parseInt(curr), 0)
}
```
문자열과 숫자열이 더해지면 문자열이 된다는 사실을 깜빡하고 있었다! 간단하게 ""를 더하는 방법도 있구나.
그리고 위 코드는 Number 대신 <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt">parseInt</a>로 문자열을 숫자열로 바꾸었다.

<br>

### 최댓값 만들기
정수 배열 numbers가 매개변수로 주어집니다. numbers의 원소 중 두 개를 곱해 만들 수 있는 최댓값을 return하도록 solution 함수를 완성해주세요.

```jsx
function solution(numbers) {
    numbers.sort((a,b) => a-b);
    return numbers[numbers.length-1]*numbers[numbers.length-2];
}
```
배열 중에서 가장 큰 값과 그 다음으로 큰 값을 곱하는 문제였다. 
그래서 오름차순으로 배열을 정렬하고 가장 뒤에 있는 값과 그 다음에 있는 값을 곱해주었다.

```jsx
function solution(numbers) {
    numbers.sort((a,b)=>b-a);
    return numbers[0]*numbers[1];
}
```
a-b로 하면 오름차순인데 b-a로 하면 내림차순이 되는구나!😮 더 간단한 방법을 배워간다.

<br>

### 특정 문자 제거하기
문자열 my_string과 문자 letter이 매개변수로 주어집니다. my_string에서 letter를 제거한 문자열을 return하도록 solution 함수를 완성해주세요.

```jsx
function solution(my_string, letter) {
    return my_string.split("").filter((x) => x !== letter).join("");
}
```
나는 split으로 문자열을 하나씩 자른 후, filter로 letter이 아닌 값만 걸러 다시 합쳐지도록 만들었다.

```jsx
function solution(my_string, letter) {
    const answer = my_string.split(letter).join('')
    return answer;
}
```
그런데 그냥 letter을 잘라 합칠 수도 있었다니! 😂 정말 효율적이다.

