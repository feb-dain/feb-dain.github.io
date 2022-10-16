---
title: "삼항 연산자, 오름차순 배열, 약수의 합 등"
layout: post
tags: Coding-Test
---

### 점의 위치 구하기 (삼항연산자)

```jsx
function solution(dot) {
    const x = dot[0];
    const y = dot[1];
    return x>0 && y>0 ? 1 : x<0 && y>0 ? 2 : x<0 && y<0 ? 3 : 4;
}
```









나는 삼항 연산자와 and 연산자를 사용했는데,
다른 사람의 코드를 보니 and 연산자를 사용하지 않은 것도 있었다.

```jsx
function solution(dot) {
    return dot[0] > 0 ? dot[1] > 0 ? 1 : 4 : dot[1] > 0 ? 2 : 3;
}
```
삼항 연산자를 이렇게도 쓸 수 있구나😮 또 하나 배워간다. 이 코드로 실행하면 속도도 빨라진다!

<br>

### 홀수 오름차순 배열

```jsx
function solution(n) {
    const answer = [...Array(n+1).keys()].filter(even => even%2 !== 0 );
    return answer;
}
```
배열을 만들고 필터로 짝수를 제외시켜줬다.

<br>

### 자릿수 더하기
정수 n이 매개변수로 주어질 때 n의 각 자리 숫자의 합을 return하도록 solution 함수를 완성해주세요.<br>
ex) n = 1234 👉 1+2+3+4 = 10

```jsx
function solution(n) {
    let answer = Array.from(String(n),Number).reduce((x, y) => x+y, 0) ;
    return answer;
}
```
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from">
  Array.from
</a>
을 사용하여 문자열로 변환 후, 붙어있는 문자열을 하나씩 자르고,
Number로 다시 숫자로 만든 다음, 배열의 합을 구해줬다.
<br>
<br>

### 짝수와 홀수 개수 각각 알아내기
정수가 담긴 리스트 num_list가 주어질 때, 
num_list의 원소 중 짝수와 홀수의 개수를 담은 배열을 return 하도록
solution 함수를 완성해보세요.

```jsx
function solution(num_list) {
    const even = num_list.filter(even => even%2 === 0).length;
    const odd = num_list.length - even;
    return [even, odd];
}
```
먼저 filter로 짝수 배열의 길이를 구했다.
홀수 개수는 원래 배열의 길이에다가 짝수의 개수를 빼줌으로써 알아냈다.

<br>

### 약수의 합
정수 n을 입력받아 n의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.<br>
ex) 12의 약수는 1, 2, 3, 4, 6, 12입니다. 이를 모두 더하면 28입니다.

```jsx
[...Array(n+1).keys()].reduce((x,y) => x+(!(n%y) && y));
```
>설명<br>
>!(n % a) this returns true only for the elements that have a 0 as modular value.<br><br>
(!(n % a) && a) is a js 'trick'.<br>
The case is that boolean expressions in javascript don't return true or false.
They return a 'truthy' or 'falsy' value which is then converted to boolean. 
So the actual returned value is the right value for && (considering both have to be truthy)
and the first thuthy value found for || (considering only one need to be truthy). 
So this basically means: if a is a modular value
(i.e. != 0) return a to add to the sum, else return 0.

<a href="https://stackoverflow.com/questions/43150520/javascript-find-the-sum-of-all-divisors-of-a-given-integer">
  stackoverflow
</a>
의 도움을 받아 풀었는데, 풀고 나니 더 좋은 풀이법이 있었다. 

```jsx
function solution(num) {
    let sum = 0;
    for (let i = 1; i <= num; i++) {
        if (num % i === 0) sum += i
    }
    return sum
}
```
배열을 만들 필요가 없으니 속도가 엄청 줄어들었다!

<br>

### 문자열 뒤집기

```jsx
function solution(my_string) {
    return my_string.split("").reverse().join("");
}
```
split을 이용해 "" 형태로 하나씩 자르고, reverse로 뒤집어준 뒤,
join을 이용해 "" 안에 하나로 합쳐주었다.(=하나의 문자열로 만들었다)<br>
<br>
아래와 같은 방법도 있었는데,
```jsx
function solution(my_string) {
    return = [...my_string].reverse().join("");
}
```
코드의 길이는 더 짧지만 시간이 더 오래 걸렸다.

<br>
<br>
