---
title: "숫자 배열 정렬, 특정 문자의 개수, 문자 교체(swap), 가위바위보 등"
layout: post
tags: Coding-Test
---

### 문자열 정렬하기(숫자만 골라 정렬)
문자열 my_string이 매개변수로 주어질 때, my_string 안에 있는 숫자만 골라 오름차순 정렬한 리스트를 return 하도록 solution 함수를 작성해보세요.

```jsx
function solution(my_string) {;
    return my_string.match(/\d/g).map(n=>Number(n)).sort((a,b)=>a-b);
}
```
나는 match를 이용해 숫자만 골라낸 다음, Number로 문자형을 숫자형으로 바꾸고 sort로 오름차순 정렬을 해주었다.








<br>

### 문자열 내 p와 y의 개수
대문자와 소문자가 섞여있는 문자열 s가 주어집니다. s에 'p'의 개수와 'y'의 개수를 비교해
같으면 True, 다르면 False를 return 하는 solution를 완성하세요.
'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다. 단, 개수를 비교할 때 대문자와 소문자는 구별하지 않습니다.

예를 들어 s가 "pPoooyY"면 true를 return하고 "Pyy"라면 false를 return합니다.

```jsx
function solution(s){
    let string = Array.from(s.toLowerCase());
    let p = string.filter(x=> x==="p");
    let y = string.filter(x => x==="y");
    return p.length === y.length;
}
```
더 깔끔하게 코드를 작성하기 위해 노력했지만, 도저히 모르겠어서 위와 같이 코드를 작성했다.

문제를 풀고 난 뒤에는 다른 사람의 코드를 볼 수 있는데, 아래와 같이 split을 이용한 사람도 있었다.
왜 생각을 못 했을까!😂 역시 망각의 동물... 잊지 않을 때까지 반복하는 수밖에 없는 거 같다.  
```jsx
function numPY(s){
    return s.toUpperCase().split("P").length === s.toUpperCase().split("Y").length;
}
```

<br>

### 자연수 뒤집어 배열로 만들기

이상하게 안 풀리던 (이제 점점 어려워져서 그런가...?) 코딩 테스트 사이에서 깔끔하게 풀린 문제라 기록해두기로 했다.
😂 기분 좋다...
```jsx
function solution(n) {;
    return Array.from(n+"", n=>Number(n)).reverse();
}
```
`숫자형+문자형` ⇒ `문자형`이 된다는 것을 이용했고, reverse로 배열을 뒤집어주었다. 

<br>

### 인덱스 바꾸기 (Swap)
문자열 my_string과 정수 num1, num2가 매개변수로 주어질 때, my_string에서 인덱스 num1과 인덱스 num2에 해당하는 문자를 바꾼 문자열을 return 하도록 solution 함수를 완성해보세요.


아래와 같이 **구조분해할당**(Destructuring assignment, 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 자바스크립트 표현식)을 이용했다.
- <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment">한국어 MDN</a>
- <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment">영어 MDN</a>
```jsx
function solution(my_string, num1, num2) {
    let arr = Array.from(my_string);
    [arr[num1],arr[num2]]=[arr[num2],arr[num1]]
    return arr.join("");
}
```

<br>

### 가위 바위 보
가위는 2 바위는 0 보는 5로 표현합니다. 가위 바위 보를 내는 순서대로 나타낸 문자열 rsp가 매개변수로 주어질 때,
rsp에 저장된 가위 바위 보를 모두 이기는 경우를 순서대로 나타낸 문자열을 return하도록 solution 함수를 완성해보세요.

```jsx
function solution(rsp) {
    let answer = Array.from(rsp, n => n === "2" ? "0" : n === "0" ? "5" : "2");
    return answer.join("");
}
```
나는 Array.from과 map, 삼항 연산자를 이용해 풀었는데,<br> 
아래와 같이 구조분해할당으로 푼 사람도 있었다.
조건이 늘어나도 간단하게 arr에 추가만 하면 되는 코드라 좋은 것 같다!
```jsx
function solution(rsp) {
    let arr = {
        2: 0,
        0: 5,
        5: 2
    };
    var answer = [...rsp].map(v => arr[v]).join("");
    return answer;
}
```

👇 `Array.from`을 이용해 위 코드를 아래와 같이 바꿔보았다.
```jsx
function solution(rsp) {
    let arr = {
        2: 0,
        0: 5,
        5: 2
    };
    return Array.from(rsp,x => arr[x]).join("");
}
```

<br>
<br>
