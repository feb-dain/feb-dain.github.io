---
title:  "VS Code 유용한 단축키와 익스텐션 "
layout: post
tags: VS-Code
---

## 단축키
<span style="background:#daebf2;"> Multi Selection </span> <br>
**👍 Ctrl+d**<br>
한 단어를 선택하고 ctrl+d 반복적으로 눌러주면 중복 단어 자동으로 모두 선택됨 ⇒ 간단 삭제, 수정가능
<br>
<br>

<span style="background:#daebf2;"> Column (box) selection </span> <br>
**Ctrl+Shift+alt+↑ or ↓**<br>

**블럭으로 전체 선택-> Shift+alt+드래그** <br>
해당 블럭 끝에 커서 생성









<details>
<summary>💡 Tip!</summary>
<div markdown="2">
블럭 끝에 커서 생성한 다음에 "Ctrl + ← or → (단어 별 이동), Ctrl + shift + ← or → (단어 선택)" 하면 편함<br>
</div>
</details>
<br>

<span style="background:#daebf2;"> Move Word </span><br>
**Ctrl+← or →**<br>
단어 별 이동<br>
<br>
<br>
<span style="background:#daebf2;"> Select Word</span><br>
**Ctrl+shift+← or →**<br>
단어 선택<br>
<br>
<br>
<span style="background:#daebf2;"> Copy Line </span><br>
**👍 Ctrl+c / Shift+Alt+↑ or ↓**<br>
라인 복사<br>
<br>
<br>
<span style="background:#daebf2;"> Cut Line </span><br>
**👍 Ctrl+x**<br>
라인 잘라내기<br>
<br>
<br>
<span style="background:#daebf2;"> Move Line Up/Down </span><br>
**👍 Alt+↑ or ↓**<br>
라인 이동<br>
<br>
<br>
<span style="background:#daebf2;"> Beginning/end of Line </span><br>
**Home, end**<br>
라인의 맨 처음, 맨 끝으로 이동<br>

**home 누르고 커서가 행 왼쪽(←)에 있으면 shift+ end,<br>
 커서가 오른쪽 끝(→)에 있다면 shift+home**<br>
행 전체 선택<br>
<br>
<br>
<span style="background:#daebf2;"> Insert Cursor </span><br>
**Alt+마우스 클릭**<br>
다중 선택<br>
<br>
<br>
<span style="background:#daebf2;"> Command palette </span><br>
**F1 / ctrl+shift+p**<br>
마우스없이 키보드로 원하는 명령어 검색하면 실행 가능<br>
(save, format, calculate, terminal...)<br>
<br>
<br>
<span style="background:#daebf2;"> Quick open </span><br>
**Ctrl+p**<br>
검색해서 원하는 파일 열기<br>
<br>
<br>
<span style="background:#daebf2;"> User setting </span><br>
**Ctrl+,**<br>
세팅 열기<br>
<br>
<br>
<span style="background:#daebf2;"> Toggle sidebar </span><br>
**Ctrl+b**<br>
사이드바 열고 닫기<br>
<br>
<br>
<span style="background:#daebf2;"> Toggle terminal </span><br>
**Ctrl+'**<br>
터미널 열고 닫기<br>
<br>
<br>
<span style="background:#daebf2;"> Keyboard shortcuts </span><br>
**Ctrl+k+s**<br>
키보드 단축키 설정<br>
<br>
<br>
<span style="background:#daebf2;"> Beginning/end of File </span><br>
**Ctrl+home, ctrl+end**<br>
파일의 맨 처음, 맨 끝으로 이동<br>
<br>
<br>
<span style="background:#daebf2;"> Insert line below </span><br>
**Ctrl+enter**<br>
코드 작성하다가 중간에 아래 줄로 이동하고 싶을 경우<br>
<br>
<br>
<span style="background:#daebf2;"> Undo last Cursor </span><br>
**Ctrl+u**<br>
이전에 있었던 커서로 이동<br>
<br>
<br>

-----

## 익스텐션
#### 1. Material Theme
테마 색상 변경
<br>
<br>

#### 2. Marterial Icon Theme
아이콘 테마, 아이콘이 조금 더 생동감 있게 바뀜
<br>
<br>

#### 3. Preitter - Code formatter
코드 포멧팅 - ctrl + , 눌러서 setting 창으로 이동<br>
>❗ Prettier 가 적용이 안 될 경우<br> 
>Default Formatter를 Prettier로 설정 변경해주면 정상적으로 동작<br>
>(Format on save 체크, tab width 2, JavaScript quote style : single로 변경)

<br>

#### 4. Bracket Pair Colorizer
괄호마다 코드에 색깔을 다르게 줌
<br>
<br>

#### 5. Indent-rainbow 
- 들여쓰기 된 부분을 무지개 색깔로 하이라이트 표시 
- 코드 읽을 때 도와줌
<br>
<br>

#### 6. Auto Rename Tag 👍
앞에 태그를 바꾸면 뒤에 태그를 자동으로 바꿔줌
<br>
<br>

#### 7. CSS Peek 
- html에서 커맨드나 컨트롤키를 누른 상태로 클릭하면 해당 css로 이동하게 해줌
- html에서 css를 금방 찾게 해줌 
<br>
<br>

#### 8. HTML CSS Support
해당 html에 적용되어있는 css 추천
<br>
<br>

#### 9. Live Server 👍
브라우저에서 바로 확인 가능
<br>
<br>

#### 10. Html to Css auto completion 
html에서 작성한 class, id 명 css에서 자동 완성
<br>
<br>

#### 11. Markdown preview
- 커멘트 팔레트에 검색하면 md 파일 미리보기 볼 수 있음
<br>
<br>

#### ♦️ Settings Sync
- 모든 세팅(익스텐션,단축키,설정값,스니펫 등)을 Github에 동기화해둘 수 있음
- 어디서든 같은 세팅을 할 수 있게 해줌
<br>

설정 동기화
   
      → 설정 동기화 할 곳에 Settings Sync 설치
    
      → Command Palette → sync 검색
    
      → Sync: 고급 옵션 → Sync: 설정 열기 
    
      → 저장했던 Gist ID & 엑세스 토큰 입력
    

![image](https://user-images.githubusercontent.com/108778921/190126892-7c890e16-c6de-4e36-9ed8-1082e1a6b51b.png)

      → OS 에 맞게 Upload Key 타이핑 하거나 Command Palette 에서 Sync 검색 후 다운로드 설정

![image](https://user-images.githubusercontent.com/108778921/190126922-29cb225a-dd9f-49fe-9629-26a6e1d2a747.png)

<br>
👀 출처!<br>
<a href="https://cho001.tistory.com/208?category=863677"> 블로그 </a><br>
<a href="https://www.youtube.com/watch?v=bS9yTI2fC0w&list=PLv2d7VI9OotQ1F92Jp9Ce7ovHEsuRQB3Y&index=10"> 유튜브 </a>
<br>

