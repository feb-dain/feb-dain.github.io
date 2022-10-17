---
title: "할인, 배열 다시 정렬(sort), 중복 배열 없애기"
layout: post
tags: Coding-Test
---

### 옷가게 할인 받기
머쓱이네 옷가게는 10만 원 이상 사면 5%, 30만 원 이상 사면 10%, 50만 원 이상 사면 20%를 할인해줍니다.
구매한 옷의 가격 price가 주어질 때, 지불해야 할 금액을 return 하도록 solution 함수를 완성해보세요.

```jsx
function solution(price) {
    return Math.floor(price >= 500000 ? price-price/5 : price >= 300000 ? price-price/10 : price >= 100000 ? price-price/20 : price);
}
```








처음에 10만원 미만의 경우를 생각하지 못하고 `price >= 100000 && price-price/20`으로 제출했다가 틀렸길래 왜 틀렸나 했다. 😂
그리고 나는 위와 같이 **price/5 = 20% | price/10 = 10% | price/20 = 5%** 로 계산했는데 
**price * 0.2 = 20% | price * 0.1 = 10% | price * 0.05 = 5%** 가 더 직관적인 것 같다.

```jsx
function solution(price) {
    const discount = price < 100000 ? 0 : price < 300000 ? price / 20 : price < 500000 ? price / 10 : price / 5;
    return Math.floor(price - discount);
}
```
어떤 사람은 위와 같이 코드를 작성했던데 가독성이 좋다고 생각한다. 코드만 봐도 '변수 discount는 가격에 따라 할인되는 금액이구나'를 알 수 있을 것 같다.
그런데 코드를 실행해보니 내가 작성한 코드의 실행 속도가 더 빨랐다.<br>
**'가독성 좋은 코드 vs 실행 속도가 빠른 코드 중 어떤 코드가 좋은 걸까?'** 라는 의문이 들었다. 그래서 찾아봤다.
- <a href="https://hackernoon.com/few-simple-rules-for-good-coding-my-15-years-experience-96cb29d4acd9">
  https://hackernoon.com/few-simple-rules-for-good-coding-my-15-years-experience-96cb29d4acd9
  </a>
<br>위 글에서는 최적화된 코드보다 가독성이 좋은 코드를 우선시했다. 
- <a href="https://betterprogramming.pub/code-readability-vs-performance-25a9ca970aca">
  https://betterprogramming.pub/code-readability-vs-performance-25a9ca970aca
  </a>
- <a href="https://stackoverflow.com/questions/183201/should-a-developer-aim-for-readability-or-performance-first">
  stackoverflow
  </a><br>
등 다양한 글을 읽어봤지만 가장 중요한 것은 정확성이라고 했다. (Correctness is the most important)
가독성이 좋으면 최적화하기 더 쉽고, 대부분의 경우 가독성을 위해 속도나 퍼포먼스를 포기하지 않아도 된다고 했다.
따라서 내 생각엔 성능/속도 면에서 그리 차이 나지 않는다면, 퍼포먼스나 속도가 중요하지 않다면 `가독성`이 우선인 게 맞는 것 같다.

그렇다면 나는 이 문제의 답을 아래와 같은 코드로 작성하는 것이 가장 좋은 것 같다.

```jsx
function solution(price) { 
    const discount = price >= 500000 ? price*0.2 : price >= 300000 ? price*0.1 : price >= 100000 ? price*0.2 : 0);
    return Math.floor(price - discount);
}
```

<br>

+맨 처음 코드로 답을 제출했을 때, 처음으로 15점을 받았다. (그 전엔 대부분 3점을 받았다) 프로그래머스 코딩 테스트 점수 산출법이 궁금해 찾아보니
>코딩 테스트의 경우 [정확성]과 [효율성]으로 구분해서 점수를 계산합니다.
[정확성] 테스트는 지원자가 제출한 코드가 문제 지문을 충분히 구현하고 있는지를 평가하며
[효율성] 테스트는 코드의 시간복잡도(코드가 문제를 해결하는데 걸린 시간이 충분히 빠른지)를 테스트합니다.

라고 한다.

<br>

### 삼각형의 완성 조건
선분 세 개로 삼각형을 만들기 위해서는 다음과 같은 조건을 만족해야 합니다.

가장 긴 변의 길이는 다른 두 변의 길이의 합보다 작아야 합니다.
삼각형의 세 변의 길이가 담긴 배열 sides이 매개변수로 주어집니다. 세 변으로 삼각형을 만들 수 있다면 1, 만들 수 없다면 2를 return하도록 solution 함수를 완성해주세요.

```jsx
function solution(sides) {
    sides = sides.sort((a, b) => a - b);
    return answer = sides[2] < sides[0]+sides[1] ? 1 : 2;
}
```
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort">
  Array.sort
</a>
를 이용하여 배열 안의 숫자를 오름차순으로 정렬하고, 3번째에 있는 숫자(sides[2])가 나머지 숫자보다 작을 경우 1을, 클 경우 2가 return 되도록 만들었다.

<br>

### 약수 구하기

```jsx
function solution(n) {
    var answer = [];
    for (let i = 1; i <= n; i++) {
        if(n % i === 0 ) answer.push(i);
    }
    return answer;
}
```
어제 <a href="https://feb-dain.github.io/ternary-operator-and-ascending-order-and-sum-of-divisors-etc/">'약수의 합'</a>에서 배웠던 방식을 응용해 약수를 구해봤다.

<br>

### 배열의 유사도
두 배열이 얼마나 유사한지 확인해보려고 합니다. 문자열 배열 s1과 s2가 주어질 때 같은 원소의 개수를 return하도록 solution 함수를 완성해주세요.

```jsx
function solution(s1, s2) {
    const combine = s1.concat(s2);          
    return combine.length - [...new Set(combine)].length;
}
```
나는 concat으로 두 배열을 합친 뒤, 합쳐진 배열의 길이에서 중복이 사라진 배열의 길이를 뺐다. (중복은 ES6 문법인 set을 이용해 없애주었다.)<br>

```jsx
function solution(s1, s2) {
    const overlap = s1.filter((x) => s2.includes(x));
    return overlap.length;
}
```
includes를 이용해 같은 원소가 있는지 확인하고(같은 원소가 있을 경우 true, 없을 경우 false 반환),
같은 원소가 있을 경우 filter로 같은 원소의 값만 걸러낸 뒤, 그 배열의 길이를 구하는 식으로 코드를 작성한 사람들도 있었다.
<br>

set을 이용하기 전, filter를 사용할 생각은 했지만 includes를 사용할 생각까진 못했었는데!
오늘도 코딩 테스트를 하면서 많이 배웠다. 😊
<br>
<br>

