---
title:  "커밋 메시지 수정, 원하는 파일만 push하기"
layout: post
tags: Git
---

### 깃 커밋 메시지 수정하기

>가장 최근 커밋한 커밋 메시지 수정
````
git commit --amend
````









터미널을 열고 `git commit --amend`를 적는다.<br>
엔터를 누르면 바로 직전 커밋 메시지를 수정할 수 있는 창으로 바뀌는데, 이 때 `i`를 눌러주면 된다.<br>
수정을 완료한 다음 esc를 누르고 `:wq`(저장 + 창 닫기)를 적어주면 된다.

> 오래된 커밋 메시지 수정 / 한 번에 여러 커밋 메시지 수정

````
git rebase -i HEAD~3
````

`HEAD~3`를 적으면 최근 커밋 3개를 보여준다.

````
pick (커밋 번호) (커밋 메시지)
pick (커밋 번호) (커밋 메시지)
pick (커밋 번호) (커밋 메시지)
````
이렇게 창이 나오면 역시 `i`를 눌러주고, pick 부분을 reword로 바꿔주면 된다.

````
reword (커밋 번호) (커밋 메시지)
pick (커밋 번호) (커밋 메시지)
reword (커밋 번호) (커밋 메시지)
````

☝ 이런 식으로!

수정을 원하는 커밋을 reword로 바꿔줬으면 esc를 누르고 `:wq`를 적는다.<br>
각 커밋 메시지를 수정할 수 있는 창이 순서대로 뜨는데<br>
이 때 `i`를 누르고 커밋 메시지를 수정하면 된다.<br>
수정을 다 한 다음에는 esc를 누르고 `:wq`를 적으면 된다.<br>
그러면 다음 커밋 메시지를 수정할 수 있는 창이 또 뜬다.<br>
위의 과정을 반복하면 끝!<br>
<br>

❗ **만약 이미 push한 깃 커밋 메시지를 수정하고 싶다면?** <br>
위의 과정을 거친 후, `git push --force origin (브랜치 이름)`을 적으면 된다.

<a href=
"https://velog.io/@mayinjanuary/git-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%84%B8%EC%A7%80-%EC%88%98%EC%A0%95%ED%95%98%EA%B8%B0-changing-commit-message">
-참고 블로그</a>

<br>

### 원하는 파일만 push 하기

````
git add (경로 / file명) (경로 / file명) (경로 / file명) ...
````

만약 Test.js 파일만 push 하고 싶다면
````
git add Test.js
````
이렇게 적고
````
git push origin (브랜치 이름) 
````
push 해주면 끝!

<a href="https://herojoon-dev.tistory.com/51">-참고 블로그</a>

<br>
<br>
