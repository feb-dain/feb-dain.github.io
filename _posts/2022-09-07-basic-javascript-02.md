---
title:  "Basic javascript 02"
layout: post
---

<div align="center">
<img src ="https://images.unsplash.com/photo-1456513080510-7bf3a84b82f8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=773&q=80" alt="studying">
<p> 자바스크립트 정리 2탄, 자바스크립트 문법(조건문 등)을 정리했다. </p>
</div>

<br>
<br>


### 1. 조건문 if문
#### 1) 단일 if문


````

      [형식]
      if(조건식=true, false | true일 경우에만 실행){
          실행문;
      }
      
      예시. (프롬프트)점수를 입력받아, 만약 숫자가 짝수면 (경고창) "짝수입니다.", 홀수면 "홀수입니다."
      var num = prompt("숫자 입력", 2);
      // 데이터형 변환 : 문자형 -> 숫자형
      num = Number(num);
      
      if(num%2==0){
          alert("짝수");
      }
      if(num%2==1){
          alert("홀수");
      }
      
````

#### 2) if~else문
    
````

      [형식]
      if(조건식=true, false | true일 경우에만 실행){
          실행문;
      }else{
          실행문;
      }
      
      var num2 = Number(prompt("숫자입력", 2));
      if(num2%2==0){
          alert("짝수입니다.");
      }else{
          alert("홀수입니다.");
      }
      /* 짝수입니다. */
      
````

#### 3) 조건식 false가 되는 경우
0, null, undefined,"  " | 나머지는 모두 true 
      
````

      if(0){
          alert("true");
      }else{
          alert("false");
      }
      /* false */

````

#### 4) else if문 : 조건이 여러 개일 경우 사용 
switch case 코드가 더 간단하지만 포괄적인 범위 지정이 불가능하다. 
````

        var grade = Number(prompt("점수입력",0));
        if(grade>=90){
            alert("A학점");
        }else if(grade>=80){
            alert("B학점");
        }else if(grade>=70){
            alert("C학점");
        }else if(grade>=60){
            alert("D학점");
        }else{
            alert("재수강");
        }

````

#### 5) 중첩 if문

````

        var dbId = "ID";
        var dbPw = "1234";

        var id = prompt("ID를 입력해주세요.","ID");
        if(dbId==id){
            var pw = prompt ("비밀번호를 입력해주세요","1234");
            if(dbPw==pw){
                alert("로그인 성공!");
            }else{
                alert("로그인 실패!");
            }
        }
        
````


### 2. 선택문 : switch~case
````
        [형식]
        switch(조건){
          case 조건N (=조건값 일치 여부):
                실행문;
                break;
          default:
                실행문;
        }

        // 입력받은 Data가 홀수인지 짝수인지 판별
        var num = prompt("좋아하는 수 입력",1);
        num = Number(num);
        switch(num%2){
            case 0:
                alert("짝수입니다.");
                break;
            case 1:
                alert("홀수입니다.");
                break;
            default:
                alert("숫자가 아닙니다.");
        }

        // 포털사이트 접속하기
        var site = prompt ("구글, 네이버, 다음 중 하나만 입력", "구글");
        switch(site){
            case "구글":
                url = "http://google.co.kr";
                break;
            case "네이버":
                url = "http://naver.com";
                break;
            case "다음":
                url = "http://daum.net";
                break;
            default:
                alert("다시 입력해주세요.");
                location.reload();
        }
     
        if(url){
            location.href = url;
        }
        
````


### 3. 반복문, while문
for문은 간결해서 가독성이 좋음

````

        // 1. 초기값
        var i = 1;
        
        // 2. 조건식 (보통 반복횟수가 온다. true값일 때만 반복)
        while(i<=5){
            document.write("안녕하세요."+i+"<br>")
            
        // 3. 증감식
            i++;
            // 반복문에서는 전위(num++;)만 사용
        }
        
````

### 4.for문
````
[형식]
  for(초깃값;조건식;증감식){
      실행문;
  }
  
  for(var i=0; i<=4; i++){
      document.write("for문 반복 횟수 : "+i+"번<br>"); /* for문 반복 횟수 : 5번 */
  }

````

이렇게 쉽게 이미지 들고 올 수도 있다. 👇
````
      for(var i=0; i<10 ; i++){
            document.write("img"+i+".jpg")
      }
````
