---
title: "최소 개수 구하기, 원하는 숫자 찾기(indexOf), 순서쌍(약수)의 개수 구하기"
layout: post
tags: Coding-Test
---

### 개미군단
개미 군단이 사냥을 나가려고 합니다. 개미군단은 사냥감의 체력에 딱 맞는 병력을 데리고 나가려고 합니다.
장군개미는 5의 공격력을, 병정개미는 3의 공격력을 일개미는 1의 공격력을 가지고 있습니다. 예를 들어 체력 23의 여치를 사냥하려고 할 때,
일개미 23마리를 데리고 가도 되지만, 장군개미 네 마리와 병정개미 한 마리를 데리고 간다면 더 적은 병력으로 사냥할 수 있습니다.
사냥감의 체력 hp가 매개변수로 주어질 때, 사냥감의 체력에 딱 맞게 최소한의 병력을 구성하려면 몇 마리의 개미가 필요한지를 return하도록 solution 함수를 완성해주세요.

= 정수 n을 만들 때 필요한 5, 3, 1의 최소 개수를 구하는 문제이다.












```jsx
function solution(hp) {
    const general = Math.floor(hp/5)
    const total = hp-general*5 === 0 ? general : (hp-general*5)%2 !== 0 ? general+1 : general+2;
    return total;
}
```
나는 정수 n을 만들 때 필요한 5의 개수를 구한 다음, 5만 이용해도 n을 구할 수 있다면 5의 개수를 그대로 반환하고
5만으로는 n을 구할 수 없을 경우, 남은 수가 홀수면 5의 개수에 +1을, 짝수면 +2를 더했다.

```jsx
function solution(hp) {
    return Math.floor(hp/5)+Math.floor((hp%5)/3)+(hp%5)%3;
}
```
더 간결하게 코드를 작성한 사람도 있었다.<br> 
5만 이용해도 n을 구할 수 있다면 위의 코드는 `5의 개수 + 0 + 0`이 될테고, 그럴 수 없다면 5와 3으로 n을 구할 수 있는지를 확인한다.
5와 3만 있어도 구할 수 있는 경우 위의 코드는 `5의 개수 + 3의 개수 + 0`을, 1도 필요할 경우 `5의 개수 + 3의 개수 + 나머지 수(1의 개수)`를 반환된다.

<br>

### 숫자 찾기
정수 num과 k가 매개변수로 주어질 때, num을 이루는 숫자 중에 k가 있으면 num의 그 숫자가 있는 자리 수를 return하고 없으면 -1을 return 하도록 solution 함수를 완성해보세요.
num에 k가 여러 개 있으면 가장 처음 나타나는 자리를 return 합니다.<br>
ex) 29183에서 1은 3번째에 있습니다.

```jsx
function solution(num, k) {
    const result = String(num).split("").indexOf(String(k));
    return result !== -1 ? result+1 : result;
}
```
정수를 split할 수 없으므로 먼저 num을 string(문자)으로 바꿔주었다.
그 다음 split을 이용해 문자열을 하나씩 잘라 하나의 배열로 만든 뒤, indexOf를 사용했다.
indexOf는 배열에 찾는 값이 없을 경우 -1를 반환하고 찾는 값이 있을 경우 해당 인덱스 값을 반환한다.
(인덱스 값은 0부터 시작하기에 +1을 해줘야 해당 자리 수가 된다.)

아래와 같이 코드를 작성한 사람도 있었다!
```jsx
function solution(num, k) {
    return num.toString().split("").map((el) => Number(el)).indexOf(k) + 1 || -1;
}
```
위 코드는 자바스크립트에서 0이 false라는 사실과 or 연산자(||)를 이용했다.
indexOf으로 인덱스 값을 구한 후, 인덱스 값에 1을 더함으로써
숫자가 있는 자리 수를 구하고 만약 배열에 찾는 값이 없을 경우 -1를 반환하게 했다. 👏
(indexOf는 -1을 반환하므로 1을 더하면 0, 즉 false가 된다. false가 되면 or 연산자 뒤의 값이 반환된다.)

위 코드를 참고해 내 코드를 바꿔주었다.
```jsx
function solution(num, k) {
    return String(num).split("").indexOf(String(k)) + 1 || -1;
}
```
아주 간결한 코드가 완성되었다. 😊

<br>

### 순서쌍의 개수
순서쌍이란 두 개의 숫자를 순서를 정하여 짝지어 나타낸 쌍으로 (a, b)로 표기합니다. 
자연수 n이 매개변수로 주어질 때 두 숫자의 곱이 n인 자연수 순서쌍의 개수를 return하도록 solution 함수를 완성해주세요.<br>
ex) n이 20 이므로 곱이 20인 순서쌍은 (1, 20), (2, 10), (4, 5), (5, 4), (10, 2), (20, 1) 이므로 6을 return합니다.

```jsx
function solution(n) {
    let answer = [];
    for (let i = 1; i <= n; i++) {
        if (n % i === 0) answer.push(i);
    }
    return answer.length;
}
```
n의 약수를 구하고 모든 약수를 빈 배열에다가 넣은 후, 그 배열의 길이를 구하면 순서쌍의 개수를 알 수 있다!
<a href="https://feb-dain.github.io/ternary-operator-and-ascending-order-and-sum-of-divisors-etc/">약수의 합을 구하는 문제를 미리 풀어서</a> 거기에서 힌트를 얻었다.

```jsx
function solution(n) {
    var answer = 0;
    for(let i = 0;i<=n;i++){
        if(n % i === 0 ){
            answer += 1
        }
    }
    return answer;
}
```
for 문이 몇 번 반복되는지를 알아냄으로써 순서쌍의 개수를 구할 수도 있다. (for 문의 반복 횟수 = 순서쌍의 개수)

다른 사람은 아래와 같이 코드를 작성했던데, 이 코드는 위의 코드들 보다 더 간결하다.
```jsx
function solution(n) {
    let answer = 0;
    for(let i=1; i<=n; i++){
        if(!(n%i)) answer++;
    }
    return answer;
}
```
자바스크립트에서 0은 false로 간주된다. if 문은 조건이 true일 경우 실행된다.
따라서 `n%i`가 0일 때마다(1부터 n까지의 수 중에 n의 약수가 나올 때마다) `answer`에 계속 1이 더해진다.
그러면 `answer`은 곧 순서쌍의 개수가 된다.

출처: 프로그래머스 코딩 테스트 연습, https://school.programmers.co.kr/learn/challenges
<br>
<br>
