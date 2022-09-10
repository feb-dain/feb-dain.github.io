---
title:  "Basic javascript 04"
layout: post
tags: JavaScript
---

<div align="center">
  
  ![image](https://user-images.githubusercontent.com/108778921/189476944-908e7ba2-0345-4603-b642-6da62790e8bf.png)
  <p>기본 자바스크립트 정리 4탄, Methods(메서드)</p>
</div>
<br>
<br>


### 1. JavaScript Date Objects
````
    // 1. 날짜 객체 생성
    let today = new Date();
    
    // 2. 날짜 관련 메서드
    let thisYear = today.getFullYear(); // 연도 (ex. 2022)
    let thisMonth = today.getMonth()+1;    // 월 0~11
    let thisDate = today.getDate();     // 날짜 1~31
    let thisDay = today.getDay();    // 요일 (일요일 0 ~ 토요일 6)
    let thisHour = today.getHours();    // 시간
    let thisMin = today.getMinutes();    // 분
    let thisSec = today.getSeconds();    // 초
    let thisMillSec = today.getMilliseconds();    //1000분의 1초
    // 1970년 1월 1일을 기준으로 밀리세컨으로 경과된 시간
    let thisTime = today.getTime();
````
````
    // Switch문을 이용해 오늘이 무슨 요일인지 알아내기
    switch(thisDay){
        case 0:
            thisDay = "일"
            break;
        case 1:
            thisDay = "월"
            break;
        case 2:
            thisDay = "화"
            break;
        case 3:
            thisDay = "수"
            break;
        case 4:
            thisDay = "목"
            break;
        case 5:
            thisDay = "금"
        break;
        case 6:
            thisDay = "토"
        break;
    }
    document.write ("오늘은 <strong>"+thisDay+"</strong>요일입니다.")
````

더 많은 JavaScript Date Objects를 알고 싶다면?
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date">&nbsp;&nbsp; Date - JavaScript | MDN </a>
