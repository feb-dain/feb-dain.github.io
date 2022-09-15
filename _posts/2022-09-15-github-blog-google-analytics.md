---
title:  "깃허브 블로그 구글 애널리틱스 적용하기"
layout: post
tags: GitHub-Blog
---

깃허브 블로그를 관리하고 방문자 수를 확인하기 위해 구글 애널리틱스를 적용하기로 했다. 구글 검색을 통해 구글 애널리틱스를 적용했는데, 바로 반영이 안되길래 '오래 걸리나?' 생각했다. 
하지만 오래 걸리는 것이 아니라 적용이 안 되어있었던 것😅 **추적 ID가 아닌 측정 ID**를 등록한 게 문제의 원인이었다. <br>

### 구글 애널리틱스에 등록했는데 적용이 안 된다면? 
1) 왼쪽 하단의 톱니바퀴 모양(관리, Admin) 클릭

![image](https://user-images.githubusercontent.com/108778921/190304192-b64d96da-99cc-479d-a11a-aaffe7008d78.png)







<br>
2) 속성 만들기(Create Property) 버튼 클릭

![image](https://user-images.githubusercontent.com/108778921/190304553-b41edf3a-e6e2-41a2-a96b-ef97d4c402be.png)

<br>
3) 순서대로 작성<br>
원하는 속성 이름 작성하고, 시간대/통화는 한국/원 설정 → 고급 옵션 보기(Show advenced options) 클릭 → 유니버설 애널리틱스 속성 만들기 오른쪽 버튼 클릭 → 웹사이트 url 작성 → 다음 버튼 클릭

![image](https://user-images.githubusercontent.com/108778921/190304815-9bded508-9437-4708-b5ec-2e7f76e9c3f7.png)

<br>
4) 비지니스 정보는 생략 가능

<br>
5) 속성 생성 완료!

<br>
6) 다시 관리 버튼 클릭

![image](https://user-images.githubusercontent.com/108778921/190304192-b64d96da-99cc-479d-a11a-aaffe7008d78.png)

<br>
7) 추적 정보(Tracking Info) > 추적 코드(Tracking Code) 클릭

![image](https://user-images.githubusercontent.com/108778921/190307534-b06d24a1-55de-4219-b35b-6218be05dad4.png)


<br>
8) 추적 ID(Tracking ID)와 범용 사이트 태그(Global Site Tag) 복사

![image](https://user-images.githubusercontent.com/108778921/190307205-6e41d4ad-5a7f-4c42-b029-45b92e558ea0.png)

<br>
9) '_includes' 폴더 안에 analytics.html 파일 생성 후, 해당 파일에 범용 사이트 태그(gtag.js) 붙여넣기<br>

```
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-000000000-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-000000000-1');
</script>
```

&nbsp;&nbsp;&nbsp;&nbsp; ❗ 이미 '_config.yml' 파일에 범용 사이트 태그가 있다면 아래와 같이 추적 코드만 붙여넣으면 된다.
 
```
google_analytics: 
  tracking_id: UA-000000000-1
```

<br>
10) '_layouts' 폴더 안 default.html파일 </footer>태그 아래에 아래 코드를 {} 괄호 안에 넣어서 붙여넣기

```
% include analytics.html % 
```

<br>
11) 바로 적용 완료! 

![image](https://user-images.githubusercontent.com/108778921/190305938-5ee2054b-c975-4797-a0b7-c9daa8586dcd.png)

<br>
