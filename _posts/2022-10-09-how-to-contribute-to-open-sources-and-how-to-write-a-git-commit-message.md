---
title: "첫 오픈 소스 기여, 좋은 커밋 메시지 작성법"
layout: post
tags: Git
---

리액트 공부를 하면서 공식 문서를 읽다가 문득 한국어 번역이 궁금해서 한국어 버전을 눌렀다.<br>
<a href="https://ko.reactjs.org/docs/rendering-elements.html">리액트-엘리먼트 렌더링</a> 👈<br>
어😮 그런데 한 문장이 번역이 안 되어 있었다. 이번 기회에 오픈 소스에 기여를 해보고자 오픈 소스 기여 방법을 검색했다.

<a href="https://soniacomp.medium.com/%EC%A3%BC%EB%8B%88%EC%96%B4-%EA%B0%9C%EB%B0%9C%EC%9E%90%EA%B0%80-%EC%98%A4%ED%94%88%EC%86%8C%EC%8A%A4-%EC%BB%A8%ED%8A%B8%EB%A6%AC%EB%B7%B0%EC%85%98-%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95-117e99540e2d">
  주니어 개발자가 오픈 소스 기여하는 방법
</a>
<br>
위 블로그를 찾았고, 상세하게 잘 설명되어 있어 덕분에 첫 오픈 소스 기여를 성공적으로 마칠 수 있었다! 나는 블로그를 참고하여 아래와 같은 방식으로 기여를 했다.<br>











<br>

1. 오픈소스 Github 레포지터리 fork
2. fork한 내 레포지터리에서 git Clone
3. 수정하고 싶은 코드 수정
4. Pull Request 버튼 클릭
5. 커밋 메시지, Pull Request 코멘트 작성

<br>

![image](https://user-images.githubusercontent.com/108778921/194741789-142c1328-f8e7-4eee-a21d-5217d790cadf.png)

하루 만에 받아들여져서 첫 오픈 소스 기여에 성공했다! 이렇게 빨리 될 줄은 몰랐는데 너무 기분 좋다.<br>

![image](https://user-images.githubusercontent.com/108778921/194742160-26edab08-708a-4544-97b3-1d5d603d974e.png)

바뀐 문서를 보니 뿌듯하고 만족스럽다. 이런 성취감 때문에 오픈 소스 기여를 하는 걸까...😂 

첫 오픈 소스 기여에서 아쉬운 점이 있었다면 바로 **커밋 메시지!**<br>
커밋 메시지를 어떻게 써야 할지 감이 안 잡혔다. 누군가는 Translate을 사용하고 누군가는 Translated를 사용했다.
처음에는 Translated로 시작하는 커밋 메시지만 봐서 '여기서는 저렇게 쓰는 게 규칙인가...?'라고 생각했다.
그래서 Translated로 커밋 메시지를 작성했다가 Translate을 사용한 기여자도 발견해서 좋은 커밋 메시지 규칙을 따르기로 했다.
커밋 메시지를 수정할 수 있어서 다행이다! 신경 쓰지 않아도 좋은 커밋 메시지를 작성할 수 있도록 노력해야겠다.

<br>

**좋은 커밋 메시지의 규칙은 다음과 같다.**<br>
  1) 제목과 본문을 한 줄 띄워 분리하기<br>
  2) 제목은 영문 기준 50자 이내로<br>
  3) 제목 첫 글자를 대문자로<br>
  4) 제목 끝에 . 금지<br>
  5) 제목은 명령조로<br>
  6) Github - 제목(이나 본문)에 이슈 번호 붙이기<br>
  7) 본문은 영문 기준 72자마다 줄 바꾸기<br>
  8) 본문은 어떻게보다 무엇을, 왜에 맞춰 작성하기<br>


**타입**<br>
feat : 새로운 기능 추가<br>
fix : 버그 수정<br>
docs : 문서 수정<br>
style : 코드 formatting, 세미콜론(;) 누락, 코드 변경이 없는 경우<br>
refactor : 코드 리팩터링<br>
test : 테스트 코드, 리팩터링 테스트 코드 추가(프로덕션 코드 변경 X)<br>
chore : 빌드 업무 수정, 패키지 매니저 수정(프로덕션 코드 변경 X)<br>
design : CSS 등 사용자 UI 디자인 변경<br>
comment : 필요한 주석 추가 및 변경<br>
rename : 파일 혹은 폴더명을 수정하거나 옮기는 작업만인 경우<br>
remove : 파일을 삭제하는 작업만 수행한 경우<br>
!BREAKING CHANGE : 커다란 API 변경의 경우<br>
!HOTFIX : 급하게 치명적인 버그를 고쳐야 하는 경우<br>

-<a href="https://cocoon1787.tistory.com/708">출처</a><br>


**추가**<br>
1. 동명사보다 명사 사용
2. 꼭 필요하지 않으면 관사는 사용하지 않는다.
3. 부정문 Don't 사용
4. 오타 수정은 Fix typo

-<a href="https://blog.ull.im/engineering/2019/03/10/logs-on-git.html">출처</a>

<br>
<br>
