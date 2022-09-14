---
title:  "Array, Object and Function"
layout: post
tags: JavaScript
---

### Array
- 하나의 변수 안에 데이터 list를 가지는 것.

`변수명[index]`<br>
→ 배열 안에 있는 것을 index 번호로 불러올 수 있음. ❗️ 주의) 컴퓨터는 0부터 셈.
```
const food = ['pizza', 'chicken', 'burger', 'noodle']
console.log(food[2])    //burger
```






`변수명.push("one")`<br> 
→ 새로운 배열 추가
```
const food = ['pizza', 'chicken', 'burger', 'noodle']
food.push('sandwich')    // ['pizza', 'chicken', 'burger', 'noodle']
```

<br>

### Object
- Property를 가진 데이터를 저장하게 해줌<br>
- Array에 넣으면 배열 안에 있는 것이 무엇인지 설명이 불가능하기에 Object 이용.<br>

```
const player = {
    name: 'tomato',
    points: 10,
    small: true,
};
```

추가 또는 변경도 가능
```
console.log(player);
player.points = 15;    //변경 {points: 15}
player.points = player.points + 15;    // {points: 30}
player.fav = 'potato';    //추가 {name: 'tomato', points: 30, small: true, fav: 'potato'}
console.log(player.fav);
```

<br>

### Function
- 계속해서 사용할 수 있는 코드 조각
- one of the fundamental building blocks in JavaScript<br>

```
function sayHello(){
	console.log("Hello!");   // 실행할 때마다 반복되는 코드
}

sayHello();    //실행
```
<br>

**argument?**
- function을 실행하는 동안 데이터를 function에 보낼 수 있게 한다.<br>

```
function func1(a, b, c) {
  console.log(arguments[0]);
  // expected output: 1

  console.log(arguments[1]);
  // expected output: 2

  console.log(arguments[2]);
  // expected output: 3
}

func1(1, 2, 3);
```
```
function sayHello(name, age){
	console.log(" Hello my name is " + name + "and I'm " + age);
}

sayHello("nico", 10);    // Hello my name is nico and I'm 10
sayHello("dal", 23);    // Hello my name is dal and I'm 23
sayHello("lynn", 21);    // Hello my name is lynn and I'm 21
```

<br>

### Object + Function
```
const calculator = {
    plus: function(a, b){
        console.log(a + " plus " + b + ":" + (a + b));    // 6 plus 2: 8
    },
    minus: function(a, b){
        console.log(a + " minus " + b + ":" + (a - b));    // 10 minus 3: 7
    },
    times: function(a, b){
        console.log(a + " times " + b + ":" + (a * b));    // 14 times 2: 28
    },
    divided: function(a, b){
        console.log(a + " divided by " + b + ":" + (a / b));    // 16 divided by 4: 4
    },
    power: function(a, b){
        console.log(a + " to the power of " + b + ":" + (a ** b));    // 5 to the power of 3: 125
    },
};
calculator.plus(6, 2);
calculator.minus(10, 3);
calculator.times(14, 2);
calculator.divided(16, 4);
calculator.power(5, 3);
```
