---
title: "CSS animation vs JS animation"
layout: post
tags: Front-End 
---

### 🤔 각각 어떤 속성을 사용하는가?
CSS : `transition`&nbsp;  `animation`<br>
JS : `setInterval()`&nbsp;  `requestAnimationFrame()` 

<br>

### CSS 애니메이션 장점













1. 미디어 쿼리로 애니메이션을 적용해 반응형으로 애니메이션을 구현하기 유용
2. 외부 라이브러리 필요 없음
3. CSS 자체가 선언형(declarative)이라 어떤 요소가 애니메이션을 가져야 한다는 직관적인 표현이 가능
4. 메인 *쓰레드가 아닌 별도의 컴포지터 쓰레드(Compositor Thread)에서 그려지기에 효율적

>💡
>*쓰레드(Thread)란?<br>
>프로세스가 할당받은 자원을 이용하는 실행 단위<br>
>스케줄러에 의해 CPU를 할당받을 수 있는 인스트럭션의 나열<br>
>프로세스의 메모리, 자원 등을 공유하므로 커널의 도움 없이 스레드간에 통신 가능<br><br>
>+프로세스란?<br>
>운영체제로부터 자원을 할당받는 작업 단위<br>
>메모리 상에서 실행중인 프로그램, 스레드는 이 프로세스 안에서 실행되는 흐름 단위<br><br>
>+인스트럭션(Instruction)이란?<br>
컴퓨터에게 일을 시키는 단위, 컴퓨터가 알아들을 수 있는 기계어로 이루어져 있는 명령<br><br>
+커널(kernel)이란?<br>
<u>컴퓨터 운영 체제의 핵심이 되는 컴퓨터 프로그램</u>, 시스템의 모든 것을 완전히 통제<br>

<br>

### JS 애니메이션 장점
1. 요소의 스타일이 변하는 순간마다 제어할 수 있어 세밀하게 애니메이션 구성 가능
2. *GPU를 통한 하드웨어 가속 제어 가능 ⇒ CSS의 특정 속성으로 인한 가속을 막아줌
    
     왜 장점인가? 하드웨어 가속이 모바일에서 성능 저하를 발생시킬 수 있기 때문
    
3. 브라우저 호환성이 CSS 트렌지션, 애니메이션 속성보다 좋다.



>💡 *GPU란?<br>
<u>Graphic Processing Unit</u>(그래픽 처리 장치)<br>
특정 단순 계산을 빠르게 함<br>
CPU에 비해 연산 장치(ALU)의 구조가 단순, 작은 제어/캐시 영역을 가짐<br><br>
vs CPU란?<br>
<u>Core Processing Unit(중앙 처리 장치)</u><br>
컴퓨터에서 사람의 뇌처럼 데이터 연산, 주변 장치 제어, 명령을 내리는 장치<br>
산술논리 장치 + 제어 장치 + 레지스터 세트 + CPU 내부 버스 등으로 구성<br>
5단계 작업 반복 : 1) 명령어 인출 2) 명령어 해독 3) 데이터 인출 4) 데이터 처리 5) 데이터 저장<br>
Instruction fetch → Instruction decode → Data fetch → Data process → Data store<br>
<br>


-<a href="https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/css-js-animation.md">참고</a>
<br>
<br>

