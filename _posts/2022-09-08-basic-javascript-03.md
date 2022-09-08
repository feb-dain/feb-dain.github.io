---
title:  "Basic javascript 03"
layout: post
---

<div align="center">
  <img src ="https://user-images.githubusercontent.com/108778921/189139969-bf92ca10-4b2c-4ed5-8153-49f0cf6ddd6e.png" title="studying">
  <p>기본 자바스크립트 정리 3탄, 함수</p>
</div>
<br>
<br>


#### 1. 버튼을 클릭할 때 마다 배경색 바꾸기
````
      // 1) 배열명 color에 문자열 red, green, blue, black, pink 저장
      var color = ["red","green","blue","black","pink"];

      // 이벤트는 꼭 두 가지가 필요함
        I. DOM 객체 (여기서는 배경색 바꾸기 버튼이 DOM 객체) II. 동작할 함수 = event listener

      var i = 0;
      // Event listener | Event Handler : 이벤트 호출시 사용되는 함수
      function chColor(){
          // Event 동작을 적용할 DOM 객체 선택
          var selectId = document.getElementById("bgc");
          // 선택자
          selectId.style.backgroundColor = color[i];
          // 이벤트가 호출할 때마다 1씩 증가
          i++;
          // 배열 이외의 값 제어
          if(i>=color.length){
              i=0;
          }
      }
        
````
````
    <div id="bgc">
        <!-- DOM객체 이벤트 발생 -->
        <button onclick="chColor();">배경색 바꾸기</button>
    </div>
````
