---
title: "정수 → 문자로 교체하기, while if 문, 배열 회전하기"
layout: post
tags: Coding-Test
---


### 외계행성의 나이
PROGRAMMERS-962 행성에서는 나이를 알파벳으로 말하고 있습니다. a는 0, b는 1, c는 2, ..., j는 9입니다. 
예를 들어 23살은 cd, 51살은 fb로 표현합니다. 나이 age가 매개변수로 주어질 때 PROGRAMMER-962식 나이를 return하도록 solution 함수를 완성해주세요.











```jsx
function solution(age) {
    const alphabet = Array.from({ length: 10 }, (VOID, index) => String.fromCharCode(index + 97));

    const ageOfPROGRAMMERS962 = Array.from(String(age), num => num = alphabet[num]).join("");

    return ageOfPROGRAMMERS962
}
```

a 부터 j까지 그냥 일일이 적을 수도 있었지만, 다른 방법을 한 번 써보았다.
`fromCharCode`를 사용하면 간편하게 알파벳을 가져올 수 있다.
알파벳 대문자는 65 ~ 90을, 소문자는 97 ~ 122 값을 갖는다.

프리코스를 하고나니 수월하게 풀렸다 😁

<br>

### 피자 나눠 먹기(2)
머쓱이네 피자가게는 피자를 여섯 조각으로 잘라 줍니다. 
피자를 나눠먹을 사람의 수 n이 매개변수로 주어질 때, 
n명이 주문한 피자를 남기지 않고 모두 같은 수의 피자 조각을 먹어야 한다면
최소 몇 판을 시켜야 하는지를 return 하도록 solution 함수를 완성해보세요.

```jsx
function solution(n) {
    let mutipleOfSix = [];
    for (let i = 1; i <= n; i++) {
        mutipleOfSix.push(6*i);
    }

    return mutipleOfSix.findIndex(num => num%n === 0)+1;
}
```
나는 `for 문`을 이용해 6의 배수(6 x n 보다 적은 수를 가진 6의 배수)가 담긴 배열을 만들고,
그 중 n을 나누었을 때 가장 먼저 나머지가 0이 나오는 수를 반환하게 만들었는데,
아래와 같이 `while 문`과 `if 문`을 사용한 사람도 있었다.

```jsx
const solution(n) {
    let piece = 6

    while(true) {
        if (piece % n === 0) {
            break
        }
        piece += 6
    }

    return piece / 6
}
```
훨씬 가독성 좋고 깔끔하다! `while 문`에다가 `if 문`을 사용할 생각을 왜 하지 못했을까😂
잘 기억해뒀다가 나중에 응용할 일이 생기면 써봐야지!

<br>

### 배열 회전 시키기
numbers 가 [1, 2, 3]이고 direction이 "right" 면 오른쪽으로 한 칸씩 회전시킨 [3, 1, 2]를 return

numbers 가 [4, 455, 6, 4, -1, 45, 6]이고 direction이 "left" 면 왼쪽으로 한 칸씩 회전시킨 [455, 6, 4, -1, 45, 6, 4]를 return

```jsx
function solution(numbers, direction) {
    if(direction === "right"){
        numbers.unshift(numbers.at(-1));
        numbers.pop();     
    }else{
        numbers.push(numbers[0])
        numbers.shift()
    }
    return numbers;
}
```

`unshift()` : 배열 맨 처음에 ()를 넣는다.
> ex) [ 1, 2, 3 ].unshift(0) → [ 0, 1, 2, 3 ]

`pop()` : 배열의 마지막 요소를 제거한다.
> ex) [ 1, 2, 3 ].pop() → [ 1, 2 ]

`push()` : 배열 맨 뒤에 ()를 넣는다.
> ex) [ 1, 2, 3 ].push(4) → [ 1, 2, 3, 4 ]

`shift()` : 배열의 첫 번째 요소를 제거한다.
> ex) [ 1, 2, 3 ].shift() → [ 2, 3 ]

이 문제에서는 위 메서드들을 사용했다. 최대한 간결하게 코드를 작성했다고 생각했는데 아니었다.

더 짧게 코드를 작성한 사람도 있었다. 👇

```jsx
function solution(numbers, direction) {
    var answer = [];

    if ("right" == direction) {
        numbers.unshift(numbers.pop());
    } else {
        numbers.push(numbers.shift());
    }

    answer = numbers;

    return answer;
}
```

굳이 배열에 넣지 않아도 되길래 필요없는 변수는 지워주었다.
```jsx
function solution(numbers, direction) {
    if(direction === "right"){
        numbers.unshift(numbers.pop());     
    }else{
        numbers.push(numbers.shift())
    }
    return numbers;
}
```
처음엔 위의 코드가 이해되지 않았다.<br>
`numbers.unshift(numbers.pop()) = [ 1, 2, 1, 2, 3 ]` 이라고 착각했기 때문이다.

하지만 아니었다. 
```jsx
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

console.log(plants.pop());
// expected output: "tomato"

console.log(plants);
// expected output: Array ["broccoli", "cauliflower", "cabbage", "kale"]
```
<p style="color: gray">( 위는 <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/pop">MDN</a> 예시이다.
역시 막힐 때는 MDN 문서를 보는 게 좋다😄 )</p>

numbers.pop()을 했을 때 **numbers** 는 [ 1, 2 ] 가 되고,
**numbers.pop()** 은 3 이 된다. 

따라서 `numbers.unshift(numbers.pop()) = [ 3, 1, 2 ]` 가 되는 것이 맞다.
이렇게 보면 더 확실하게 이해가 된다! 👇 
> numbers.unshift(numbers.pop()) = [ 1, 2 ].unshift(3)


MDN 문서를 보고 하나씩 분석했더니 이해가 잘 되었다.

<br>

출처: 프로그래머스 코딩 테스트 연습, https://school.programmers.co.kr/learn/challenges
