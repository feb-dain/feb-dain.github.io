---
title:  "Basic javascript 01"
layout: post
---

결국 리액트(React)도 자바스크립트의 라이브러리 중 하나이다. 리액트를 잘 다루기 위해서는 자바스크립트(기본)를 잘 다루어야 한다. 리액트 공부를 하면서 자바스크립트 기본기를 복습하니 이해가 더 잘 되는 기분이다. 리액트 공부를 하면서 틈틈이 자바스크립트 공부도 해야겠다. 리액트를 이용해 자유자재로 내가 원하는 것을 만들 수 있다면 얼마나 좋을까, 얼마나 편리할까. 내가 바라는 미래의 모습을 기대하며 꾸준히 공부해 나가야지. 깃허브 블로그를 생성하고 1일 1커밋을 다짐하면서 쓰는 첫 글이 기본 자바스크립트라서 더 뜻깊은 것 같다. 이만 각설하고, 그동안 배웠던 자바스크립트를 보기 편하게 정리해야지. 


#### 0. body 영역= 도큐먼트(DOM)에 출력하기

#### 1. 논리형 데이터(Boolean) = true, false
     
````

   var bool = true;    /* 1과 같음 */
   var bool2 = false;    /* 0과 같음 */
   
````

#### 2. 데이터형 변환
````

   var com1 = 20;
   var com2 = "30";
   var com3 = "40";

   // (중요) + 연산시 데이터형이 하나라도 문자열일 경우, 무조건 문자열 결합으로 연산
   var result4 = com1+com3;    /* 2040 */

   // 데이터형 변환 : 문자형 -> 숫자형
   com2 = Number(com2);
   com3 = Number(com3);
   var result = com3 + com4;    /* 70 */
   
````

#### 3. 변수의 재사용성
````

   var a = "<";
   var b = "h";
   var c = "1";
   var d = ">";
   var e = "/";
   var result = a+b+c+d + "자바스크립트" + a+e+b+c+d;    /* <h1>자바스크립트</h1> */
   
````

#### 4. 데이터 (Typeof)
1) 논리형(Bloolean)
````

   var bool = true;
   var boolTwo = false;
   
````
        
2) undefined
````

   var undefined;
        
````

3) null
````

   var clear = null;
   console.log(typeof(clear));    /* object */
 
 ````

#### 5. 산술 연산자 : 나머지값 구하기(%)
ex) num1 % num3;

#### 6. 복합 대입 연산자
기존 Data에 변수값 추가 | 변수명 한 번만 사용하여 Data 누적시키기 위해 사용

 ````
 
   var num1 = 10;
   var num2 = 3;
   num1 += num2;    /* 13 */
   num1 -= num2;    /* 10 */
   num1 *= num2;    /* 30 */
   num1 /= num2;    /* 10 */
   num1 %= num2;    /* 1 */
   
   
   /* 응용 */
   var table = '<table width="300" border="1">';
        table += '<tr><td>1</td><td>2</td><td>3</td><td>4</td></tr>';
        table += '<tr><td>1</td><td>2</td><td>3</td><td>4</td></tr>';
        table += '<tr><td>1</td><td>2</td><td>3</td><td>4</td></tr>';
        table += '</table>';
   document.write(table);
        
       var img = '<div>';
            img += '<img src="./images/norway.webp" alt="노르웨이 풍경 이미지">';
            img += '</div>';
       document.write(img);
        
 ````
        
#### 7. 증감 연산자
 ````
 
   var num1 = 20;
   var result = null;

   // 1. 증감연산자 전위(前位) : 초기값을 처음에 무조건 사용할 때 사용
   result = num1++;
     /* result : 20, num2 : 21 */
     /* result : 20, num2 : 21 */

   // 2. 증감연산자 후위(後位) : 일반적인 증감연산자
   result = ++num1;
     /* result : 22, num2 : 22 */
     /* result : 22, num2 : 22 */
          
 ````
          
#### 8. 비교 연산자
 ````
 
   var a = 10;
   var b = 20;
   var c = 10;
   var d = '20';
   var result = null;

   // 비교연산자 : 논리값 결과 반환 = true, false
   result = a > b;    /* false */
   result = a < b;    /* true */
   result = a >= c;    /* true */
   
   // 데이터 형과 상관없이 숫자일 경우 true 반환
   result = b == d;    /* true */
   
   // 데이터 형까지 일치해야 true 반환
   result = b === d;    /* false */
   
   // (논리부정)데이터 형과 상관없이 숫자일 경우 false 반환
   result = b != d;    /* false */
   
   // (논리부정)데이터 형까지 일치해야 false 반환
   result = b !== d;    /* true */ 
   
 ````
 
 <h4> 9. 논리 연산자 </h4>
  ````
  
   var a,b,c,d,result; 
   a = 10;
   b = 20;
   c = 0;
   d = 'javaScript';
   result = null;

   /* 1.논리연산자(논리합) : || or연산자로 논리식 중 하나라도 true면 true */
   result = b > a || b <= c || a > c;    /* true */

   /* 2.논리연산자(논리합) : && and연산자로 모두 true면 true */
   result = a <= b && b >= c && c < a;   /* true */

   /* 3.논리연산자(논리부정) : ! not연산자 단항 연산자 = 부정 */
   result = !(a < b);    /* false */


   // (중요) 삼항조건연산자
   // [형식] 조건식 ? 자바스크립트 코드1 (조건식의 값이 true일 경우 실행) :자바스크립트 코드2 (조건식의 값이 false일 경우 실행);
   var int = 10;
   var int2 = 20;
   var tf = int>int2 ? 'true' : 'false'; /* false */
   
 ````
 
<h4> 10. Alert, confirm, prompt </h4>
 ````
 
   // Alert : alert("  "); 
   알림창, 사용자에게 중요한 내용이나 경고창을 띄워줄 때 주로 사용하는 함수로 가장 많이 사용.
   
   // Confirm : confirm("  ");
   사용자에게 Ture 또는 False 값을 리턴받을 수 있는 팝업창을 띄워준다. ( 확인 : True, 취소 : False )
   
   // Prompt : prompt("메시지","디폴트 값");
   var name = prompt("당신의 이름은 무엇입니까?","이름");
   var gender = window.prompt("당신의 성별은 무엇입니까?","성별")
   document.write("<strong>"+name+"</strong>님 반갑습니다.<br>");
   document.write("<em><strong>"+name+"</strong></em>님의 성별은 <strong>"+gender+"</strong>입니다.");

   사용자가 입력한 값이 출력된다.
        
 ````
