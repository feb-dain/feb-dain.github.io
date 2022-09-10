---
title:  "Basic javascript 04"
layout: post
tags: JavaScript
---

<div align="center">
  <img src ="https://images.unsplash.com/photo-1488190211105-8b0e65b80b4e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" title="studying">
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

<br>

### 2. String Objects
````
    let str = "Hello Thank you good luck to you ";
    
    // a. 문자열에서 해당 인덱스 번호에 해당하는 문자를 반환
    document.write(str.charAt(10),"<br>");     // k

    // b. 문자열에서 왼쪽부터 찾을 문자와 제일 먼저 일치하는 문자의 인덱스 번호를 반환
    document.write(str.indexOf("you"),"<br>");    // 12

    // c. 문자열에서 오른쪽부터 찾을 문자와 제일 먼저 일치하는 문자의 인덱스 번호를 반환
    document.write(str.lastIndexOf("you"),"<br>");    // 29

    // d. 문자열에서 왼쪽부터 바꿀 문자와 일치하는 문자를 찾아 제일 먼저 찾는 문자를 새 문자로 치환 ⭐
    document.write(str.replace("you","me"),"<br>");    // Hello Thank me good luck to you

    // e. 문자열에서 문자를 자른 후 남는 문자를 반환 ⭐
    document.write(str.slice(3,7),"<br>");    // 인덱스 3부터 7이전까지 추출 : lo T

    // f. 문자열에서 지정한 문자 개수만큼 문자열 반환 ⭐
    document.write(str.substr(21,4),"<br>");    // 인덱 21부터 4개 글자를 반환 : luck 

    // g. 문자열에서 영문 대문자를 모두 소문자로 치환 ⭐
    document.write(str.toLowerCase(),"<br>");    // hello thank you good luck to you

    // h. 문자열에서 영문 소문자를 모두 대문자로 치환
    document.write(str.toUpperCase(),"<br>");    // HELLO THANK YOU GOOD LUCK TO YOU

    // i. 문자의 앞 또는 뒤에 공백 문자열 삭제
    document.write(str.trim());    // Hello Thank you good luck to you

    // + 문자열 개수 반환
    document.write(str.length);    // 33
````
````
    // 입력받은 전화번호 뒷자리 별표(*)로 가리기
    let phone = prompt("전화번호를 입력하세요.","010-1234-5678");
    let result = phone.replace(phone.substr(9,4),"<span>****</span>");
    document.write("전화번호: "+result);    /* 전화번호: 010-1234-**** */
````
<br>

### 3. Browser
````
    // 1.location = 브라우저 주소창
    현재 주소 : location.href
    현재 사용하는 프로토콜 : location.protocol
    현재 사용하는 포트 번호 : location.host

    // 2. navigator = 브라우저 정보
    브라우저 코드명 : navigator.appCodeName 
    브라우저 이름 : navigator.appName 
    브라우저 버전 : navigator.appVersion 
    브라우저 사용 언어 : navigator.language
    브라우저 엔진 이름 : navigator.product 
    운영체제 환경 : navigator.platform 
    운영체제 종합 정보 : navigator.userAgent 
````
````
    // Windows 사용자 찾기
    let client = navigator.userAgent.toLowerCase();
    let result = client.indexOf("windows");
    if(result){
        document.write("Windows 사용자");
    }else{
        document.write("windows 이외의 사용자");
    }
````
<br>

### 4. Screen
````
    // 사용자의 화면 크기나 정보를 알아낼 수 있다.
    screen.width;    // 스크린 너비
    screen.height;    // 스크립 높이
    screen.availWidth;    // 유효한(작업 표시줄 등 제외) 스크린 너비
    screen.availHeight;    // 유효한(작업 표시줄 등 제외) 스크린 높이
````
<br>

### 5. SetInterval
````
    <script>
      let addNum = 0;
      let subNum = 1000;
      // 3초마다 1씩 더하기
      let plusNum = setInterval(function(){
          addNum++;
          console.log("addNum : "+addNum);    /* 1 -> 2 */
      },3000);

      // 2초마다 1씩 빼기
      let minusNum = setInterval(function(){
          subNum--;
          console.log("minusNum : "+subNum);    /* 999 -> 998 */
      },2000);
    <script>
    
    <body>
      <!-- 인터벌 멈추게 하기 -->
      <button onclick="clearInterval(plusNum);">setInterval_STOP</button>
      <button onclick="clearInterval(minusNum);">setInterval_STOP2</button>
    </body>
````
<br>

### 6. SetTimeout
````
    // 3초 뒤 알림창 나타남
    setTimeout(function(){
        alert("까꿍");
    },3000);
````
<br>

### 7. SetAttribute : 속성값을 바꿔줌
````
    // this.속성(src)으로 할당. 동적 변수 src를 변수 newPic에 저장
    let newPic = this.src;
    // setAttribute("바꿀 속성명",바뀌는 변수) 
    바꿀 변수.setAttribute("src",newPic);
````
`❗ this : 함수 내에서의 함수 호출 맥락(context). 함수를 어떻게 호출하느냐에 따라서 this가 가리키는 대상이 달라진다.
Window일 수도, 객체 자신일 수도 있다.`

<br>
