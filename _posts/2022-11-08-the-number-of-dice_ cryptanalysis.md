---
title: "상자를 채울 수 있는 주사위의 개수, 문자열의 n배수 번째 글자만 추출하기(+= 사용)"
layout: post
tags: Coding-Test
---

### 주사위의 개수
머쓱이는 직육면체 모양의 상자를 하나 가지고 있는데 이 상자에 정육면체 모양의 주사위를 최대한 많이 채우고 싶습니다. 상자의 가로, 세로, 높이가 저장되어있는 
배열 box와 주사위 모서리의 길이 정수 n이 매개변수로 주어졌을 때, 상자에 들어갈 수 있는 주사위의 최대 개수를 return 하도록 solution 함수를 완성해주세요.







![image](https://user-images.githubusercontent.com/108778921/200591653-df8bfa98-db84-42df-af64-f422f6352fc8.png)

```jsx
function solution(box, n) {
    let answer = box.map((x) => ~~(x/n)).reduce((acc, cur) => acc * cur);
    return answer;
}
```
box 배열 안에 있는 각각의 숫자를 n으로 나누고, 배열을 모두 곱하면 되겠다는 생각을 했다. 
그래서 `map`을 이용해 각각의 숫자를 n으로 나누고 `~~` 물결 연산자, tilt(틸트) 연산자를 이용해 소수점 자리를 없애주었다.
그리고 나서 `reduce`를 이용해 배열 안에 있는 숫자를 모두 곱해주었다.

<br>

### 암호 해독
군 전략가 머쓱이는 전쟁 중 적군이 다음과 같은 암호 체계를 사용한다는 것을 알아냈습니다.

암호화된 문자열 cipher를 주고받습니다.
그 문자열에서 code의 배수 번째 글자만 진짜 암호입니다.
문자열 cipher와 정수 code가 매개변수로 주어질 때 해독된 암호 문자열을 return하도록 solution 함수를 완성해주세요.

![image](https://user-images.githubusercontent.com/108778921/200592447-a8f01f5a-992e-454c-8a7a-f3a6a26d24a1.png)


```jsx
function solution(cipher, code) {
    let answer = [];
    for(let index = 1; index <= cipher.length ; index++) {
        index % code === 0 && answer.push(cipher[index-1])
    }
    return answer.join("");
}
```
어떻게 문제를 풀까 고민하다가 `for 문`과 `push` 메서드를 이용해 문제를 풀기로 했다.
`for 문`을 이용해 index를 1부터 cipther의 배열 길이까지 하나씩 더하도록 만들었다.
그리고 index가 하나씩 더해질 동안
index/code의 나머지가 0이라면
cipther의 인덱스 번호 'index-1'에 해당하는 값이
빈 배열 answer에 들어가도록 했다.
> `&&` (and) 연산자는 `if 문`을 대신해서 쓸 수 있다. (true라면) && (이 값을 반환한다) 

그리고 answer 배열을 ""로 `join`해 합쳐진 문자를 반환하도록 했다.

풀고 나니 더 좋은 코드가 눈에 보였다.

```jsx
function solution(cipher, code) {
  var answer = "";
  for (let i = code - 1; i < cipher.length; i += code) {
    answer += cipher[i];
  }
  return answer;
}
```
위처럼 푼 사람이 있었는데 훨씬 더 간단해 보였다.
index를 code-1 값으로 설정하고, index를 하나씩 더하는 게 아닌 code의 값만큼 더하고,
빈 문자형인 answer에다가 code의 배수 번째 글자만 더하게 하는 방법이었다.
이렇게 풀 수도 있구나! 모르는 메서드나 연산자는 없는데 이렇게 풀 생각은 못했다.
다른 사람들의 코드를 분석하고 배우는 건 정말 재밌는 것 같다. 흥미롭다. 😊 

<br>
<br>
