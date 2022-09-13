---
title:  "Array와 Object"
layout: post
tags: JavaScript
---

## Array
하나의 변수 안에 데이터 list를 가지는 것.

`변수명[index]`<br>
→ 배열 안에 있는 것을 index 번호로 불러올 수 있음. ❗️ 주의) 컴퓨터는 0부터 셈.
```
const food = [pizza, chicken, burger, noodle]
console.log(food[2])    //burger
```






`변수명.push("one")`<br> 
→ 새로운 배열 추가
```
const food = [pizza, chicken, burger, noodle]
food.    //b
```

## Object
Property를 가진 데이터를 저장하게 해줌<br>
Array에 넣으면 배열 안에 있는 것이 무엇인지 설명이 불가능하기에 Object 이용.<br>

```
const player = {
    name: "tomato",
    points: 10,
    small: true,
};
```

추가 또는 변경도 가능
```
console.log(player);
player.points = 15; //변경
player.points = player.points + 15; // 15+15=30
player.fav = "potato"; //추가
console.log(player.fav);
```
