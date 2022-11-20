---
title:  "n번째로 큰 수, 작은 수 찾기"
layout: post
tags: Coding-Test
---

우테코 프리코스에 집중하느라 코딩 테스트 연습을 잘 못하고 있다. 우테코 끝나고 나면 열심히 해야지! 💪

### 최댓값 만들기 (2)
정수 배열 numbers가 매개변수로 주어집니다. numbers의 원소 중 두 개를 곱해 만들 수 있는 최댓값을 return하도록 solution 함수를 완성해주세요.








![image](https://user-images.githubusercontent.com/108778921/202905760-dd72a62a-1269-49b5-8471-868138f794ab.png)

주의할 점은 **중복값이 있을 수 있다는 것**이었다.
filter를 썼다가 실패했는데, 실패한 덕분에 더 좋은 코드를 작성할 수 있었다!

```jsx
function solution(numbers) {
    const sort = numbers.sort((a,b) => b-a);
    
    return Math.max(sort[0]*sort[1], sort.at(-2)*sort.at(-1));
}
```
`sort`를 이용해 배열을 내림차순으로 정렬하고,
가장 큰 수와 두 번째로 큰 수를 곱한 값과 가장 작은 수와 그 다음으로 작은 수를 곱한 값 중 더 큰 수를 return하도록 했다. 

8점 야호😄

<br>

출처: 프로그래머스 코딩 테스트 연습, https://school.programmers.co.kr/learn/challenges
<br>
<br>
