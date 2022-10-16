---
title: "프로그래머스에서 첫 코딩 테스트"
layout: post
tags: Coding-Test
---

나도 이제 코딩 테스트 공부를 해봐야겠다는 생각이 들어 프로그래머스에 들어가 코딩 테스트를 하기 시작했다.
아직 입문이라 재밌고, 다른 사람 풀이 코드 보는 것도 흥미롭다. '어떻게 저렇게 코드를 작성할 생각을 했을까?' 신기하기도 했다.
그리고 오늘 푼 코딩 테스트 중에 흥미로운 풀이를 블로그에 기록해 보기로 했다.








### 각도기
각에서 0도 초과 90도 미만은 예각, 90도는 직각, 90도 초과 180도 미만은 둔각 180도는 평각으로 분류합니다.
각 angle이 매개변수로 주어질 때 예각일 때 1, 직각일 때 2, 둔각일 때 3, 평각일 때 4를 return하도록 solution 함수를 완성해주세요.
<br><br>
예각 : 0 < angle < 90 <br>
직각 : angle = 90 <br>
둔각 : 90 < angle < 180 <br>
평각 : angle = 180 <br>

```jsx
function solution(angle){
  const answer = [ 0, 90, 91, 180 ].filter(x => angle >=x).length;
  return answer;
}
```

'삼항 연산자(또는 if else)로 풀 생각만 했는데, 이런 식으로 풀 수도 있구나' 정말 새로웠다.

<br>

### 배열의 평균값 구하기 (=배열의 합 구하기!)
정수 배열 numbers가 매개변수로 주어집니다. numbers의 원소의 평균값을 return하도록 solution 함수를 완성해주세요.<br>
```jsx
function solution(numbers) {
    const answer = numbers.reduce((prev, cur)=>{return (prev += cur);},0) / numbers.length;
    return answer;
}
```
나는 이렇게 <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce">reduce</a>를 사용해 풀었는데
```jsx
function solution(numbers){
  var answer = 0;
  for(i of numbers){
    answer += i
  }
  return answer / numbers.length;
}
```
위와 같이 <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of">for of 문</a>으로 푼 사람도 있었다. 😮
<br>
<br>
+추가<br>
```jsx
function average(array){
  return array.reduce((a, b) => a + b) / array.length;
}
```
이렇게 더 간결하게 코드를 작성할 수 있다. 그리고 초깃값이 0이면 생략해도 괜찮은 것 같다.
또 `for ... of`문 보다 reduce로 배열의 합을 구하는 게 (코드 속도가) 더 빠르다!

<br>

### 짝수의 합
정수 n이 주어질 때, n이하의 짝수를 모두 더한 값을 return 하도록 solution 함수를 작성해주세요.
```jsx
function solution(n){
  var half = Math.floor(n/2);
  return half*(half+1);
}
```
나는 새로운 배열을 만들고, filter로 짝수를 걸러내서, 걸러낸 배열의 합을 구했는데
이렇게 간단하게 코드를 작성할 수 있었다니...🤣 <br>
<br>

코딩 테스트를 하면서, 다른 사람들의 풀이를 보면서 많이 배우는 것 같다. 그래서 코딩 테스트를 하고 공부를 하는구나 생각했다.
나도 클린 코딩을 할 수 있도록, 효율적인 코드를 작성할 수 있도록 이제부터 매일 조금씩이라도 코딩 테스트를 해야겠다!

<br>
<br>
