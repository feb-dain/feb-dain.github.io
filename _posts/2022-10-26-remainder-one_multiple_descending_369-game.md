---
title: "나머지가 1이 되는 수, 배수 구하기, 내림차순 정렬, 369"
layout: post
tags: Coding-Test
---

### 나머지가 1이 되는 수 찾기
자연수 n이 매개변수로 주어집니다. n을 x로 나눈 나머지가 1이 되도록 하는 가장 작은 자연수 x를 return 하도록 solution 함수를 완성해주세요. 답이 항상 존재함은 증명될 수 있습니다.

3 ≤ n ≤ 1,000,000







```jsx
function solution(n) {
    for(let i=2;i<n;i++){
        if(n%i === 1)
            return i
    }
}
```
나는 `for 문`과 `if 문`을 이용해 나머지가 1이 되는 수를 찾았다. 

```jsx
function solution(n, x = 1) { 
    while (x++) { 
        if (n % x === 1) { 
                return x;       
              }   
        } 
}
```
for 문 대신 `While`을 쓰면 코드가 더 간결해진다! 코드 실행 속도는 근소하게 while이 더 빠르다. 
코딩 테스트를 하면서 다른 사람들의 좋은 코드를 많이 볼 수 있어 공부가 많이 된다!

<br>

### x만큼 간격이 있는 n개의 숫자
함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다.
다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

제한 조건<br>
- x는 -10000000 이상, 10000000 이하인 정수입니다.
- n은 1000 이하인 자연수입니다.

= x의 배수를 구하는 문제이다.

양수만 있었다면 편했을 텐데 음수가 있어서 좀 헤맸다. 음수가 있어서 너무 어렵게 생각했다. 쉽게 생각하면 되는데...😅
그리고 `push` 사용법을 착각해서 문제를 푸는데 시간이 좀 걸렸다.

처음에 변수 없이 `[].push`를 했다가 '왜 안 되지? 뭐가 문제지? push가 아닌가?' 등 각종 의문이 생겼다.
막혔을 때 바로 MDN 문서를 확인했어야 했는데... '이게 아닌가 보다' 하고 다른 방법을 찾아 돌아다녔다. 😂
뒤늦게 MDN 문서를 확인해 보니 **push를 잘못 사용하고 있었다!**

```jsx
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count);
// expected output: 4
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows"]
```
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push">MDN 문서</a>를 보자
내 실수가 뭐였는지 알게 됐다. MDN 문서에서 가져온 코드로 예를 들면
Retrun에 `animals`가 아닌 `count`를 넣어놓고 " 왜 push가 안 되는 거야~~ " 하고 있었다... 

`push`를 제대로 쓰니 문제가 수월하게 풀렸다.
```jsx
function solution(x, n) {
    let answer = [];
    for(let i=1;i<=n;i++){
        answer.push(x*i)
    }
    return answer;
}
```
변수 answer에 빈 배열( [] )을 두고, `for 문`을 이용했다.<br>
x와 i(1 ~ n까지의 수)를 곱한 다음, `push`를 이용해 곱해진 수를 변수 answer(빈 배열)에 하나씩 넣었다.<br>
`for 문` 안에서 `push`가 진행되기 때문에 변수 i가 1씩 증가될 때마다 빈 배열에 x와 i를 곱한 수가 하나씩 들어가게 된다.<br>  
x가 음수더라도 i가 양수이기 때문에 곱해도 음수가 나온다!

문제를 풀고나니 아래와 같이 코드를 작성한 사람도 있었다.
```jsx
function solution(x, n) {
    return Array(n).fill(x).map((v, i) => (i + 1) * v)
}
```
신기... `Array(n)`을 사용하면 n만큼 배열 안에 null이 생기는데
([null, null, null] 이런 식으로)<br>
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill">fill</a>을 이용해 null을 x값으로 채워주고<br>
`map`을 이용해 각 x에다가 '1씩 증가하는 가상의 값 i'을 곱해준 코드이다.

엄청 간결하다! 하지만 실행 속도는 for 문이 더 빠르다.

<br>

### 정수 내림차순으로 배치하기
함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

```jsx
function solution(n) {
    let answer = (n+"").split("").sort((a,b) => b-a).join("");
    return answer/1;
}
```
숫자형에 문자형("")을 더해줘 문자형으로 바꾸고,
`split`으로 문자열을 하나씩 나눈 다음, `sort`로 내림차순 정렬하고 `join`으로 합쳐주었다.
그리고 나누기 1을 함으로써 문자형을 다시 숫자형으로 바꿔줬다.

속도를 위해 위와 같이 코드를 작성했지만,
```jsx
function solution(n) {
    let answer = String(n).split("").sort((a,b) => b-a).join("");
    return Number(answer);
}
```
이렇게 코드를 작성하는 게 많은 사람들이 이해하기 좋을 것 같다. 

String, Number를 쓰면 설명 필요 없이 그냥 봤을 때 이해되니까 더 좋은 코드가 아닐까... 생각한다.
사실 이 정도는 개인 취향대로 쓰면 될 것 같긴 하다. 속도가 더 중요하면 ""와 사칙연산을 써서 문자형 ↔ 숫자형 변환하고
가독성 좋은 코드를 작성하고 싶으면 String, Number를 사용하는 게 더 좋은 것 같다!<br>
>틀린 게 있다면 편하게 알려주세요!

<br>

### 369 게임
머쓱이는 친구들과 369게임을 하고 있습니다. 369게임은 1부터 숫자를 하나씩 대며 3, 6, 9가 들어가는 숫자는 숫자 대신 3, 6, 9의 개수만큼 박수를 치는 게임입니다.
머쓱이가 말해야하는 숫자 order가 매개변수로 주어질 때, 머쓱이가 쳐야할 박수 횟수를 return 하도록 solution 함수를 완성해보세요.

<span style="color:gray">그나저나 왜 머쓱이로 이름을 지은 걸까...? 급 궁금증이 생겼다.😂 머쓱이... 귀엽</span>

```jsx
function solution(order) { 
    return String(order).split("").filter(n => ["3", "6", "9"].includes(n)).length;
}
```
나는 이렇게 order를 문자형으로 바꾸고<br>
`split`으로 문자열을 하나씩 자른 뒤,<br>
`filter`로 3, 6, 9에 해당하는 문자만 골라내고<br>
>filter 조건에 includes를 이용. filter는 false 값은 걸러내고 true 값만 반환.<br>
> [ "3", "6", "9" ].includes(n) = "3", "6", "9" 셋 중 하나가 포함될 경우 true

`length`로  배열의 길이를 구했다.

아래와 같이 유니코드를 이용해 문제를 푼 사람도 있었다.
```jsx
function solution(order) {
    var answer = [...order.toString().matchAll(/[3|6|9]/g)].length;
    return answer;
}
```
order를 문자형으로 바꾸고 3, 6, 9에 해당되는 값을 찾아 배열을 만든 뒤, 그 배열의 길이를 구한 코드이다. 

<br>
<br>
