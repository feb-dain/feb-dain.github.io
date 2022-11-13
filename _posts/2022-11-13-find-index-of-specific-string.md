---
title:  "특정 문자의 인덱스 번호 찾기"
layout: post
tags: Coding-Test
---

### 서울에서 김서방 찾기
String형 배열 seoul의 element중 "Kim"의 위치 x를 찾아, "김서방은 x에 있다"는 String을 반환하는 함수, solution을 완성하세요. 
seoul에 "Kim"은 오직 한 번만 나타나며 잘못된 값이 입력되는 경우는 없습니다.













```jsx
function solution(seoul) {
    let answer = seoul.indexOf("Kim");
    return `김서방은 ${answer}에 있다`;
}
```

Seoul은 배열이므로 indexOf를 사용하면 
쉽게 특정 문자의 인덱스를 찾을 수 있다.

```jsx
["a", "b", "c", "d"].indexOf("c")  // 2
```

<br>

출처: 프로그래머스 코딩 테스트 연습, https://school.programmers.co.kr/learn/challenges
<br>
<br>
