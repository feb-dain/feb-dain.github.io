---
title:  "Basic javascript 03"
layout: post
tags: JavaScript
---

<div align="center">
  <img src ="https://user-images.githubusercontent.com/108778921/189139969-bf92ca10-4b2c-4ed5-8153-49f0cf6ddd6e.png" title="studying">
  <p>기본 자바스크립트 정리 3탄, 함수와 배열</p>
</div>
<br>
<br>


### 예시를 통해 함수 이해하기

#### 1. 버튼을 클릭할 때 마다 배경색 바꾸기
````
      <script>
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
      </script>

      <body>
          <div id="bgc">
              <!-- DOM객체 이벤트 발생 -->
              <button onclick="chColor();">배경색 바꾸기</button>
          </div>
      </body>
````

#### 2. 매개변수 인수(인자)
````
        <script>
            // (name, area) -> 매개변수명
            function info(name,area){
                document.write("이름? "+name+"<br>");
                document.write("사는 곳? "+area+"<br>");
            }

            // 반드시 호출하는 곳에서 매개변수의 값을 넘겨줌
            info("홍길동","제주도");

            // 버튼 클릭시
            function info2(name){
                document.write("안녕하세요. "+name+"입니다.<br>");
            }
            function info3(area){
                document.write("사는 곳은 "+area+"입니다.");
            }
        </script>
        
        <body>
            <!-- 호출하는 곳에 매개변수 값을 넘겨줌_2
            <button onclick="info2('홍길동');">버튼1</button>
            <button onclick="info3('제주도');">버튼2</button>
        </body>
````

#### 3. Return : 호출한 곳에 가지고 있던 값을 돌려줌
````
        var ten = 10;
        var sum = 0;
        var mul = 0;
        function cal(num){
            sum = num + ten;
            mul = num * ten;
            return mul;    //첫번째 return을 만나면 빠져나온다. top-down 적용 안 됨
            return sum;
        }
        document.write(cal(100));    /* 1000 */
````

return; : null을 반환.
return true/false 값을 명시해주는 것이 좋다. 

<br>

### 예시를 통해 배열(Array) 이해하기
````
        var test = ["국어","영어","수학","과학","사회"];

        // 배열에 있는 모든 데이터 출력
        // document.write(test);    /* 국어,영어,수학,과학,사회 */
        for(var i=0; i<test.length; i++){
            document.write(test[i]);    /* 국어영어수학과학사회 */
        }
````

#### 1. Random
````
    // 점심 메뉴 정하기
    // 1. 배열에 저장
    var menu = ["김치찌개","삼겹살","피자","초밥","돈가스","닭강정","치킨","된장찌개"];
    
    // 2. 랜덤값 만들기
    var menuSelect = Math.floor(Math.random()*menu.length);
    var result = menu[menuSelect];
    document.write("<h1>오늘의 점심 메뉴는 <em>"+result+"</em></h1>")
````
`❗ ceil : 올림, round : 반올림, floor : 내림`
