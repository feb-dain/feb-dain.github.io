---
title:  "깃허브 블로그 댓글 기능 추가, 검색 엔진에 등록하기"
layout: post
tags: GitHub-Blog
---

<p></p>
<p>깃허브 블로그를 만들고 나니 '댓글 기능도 있었으면 좋겠고, 구글 검색에도 걸렸으면 좋겠는데...'라는 생각이 들었다.<br>
구글 검색을 해보니 많은 개발자들이 방법을 정리해둔 블로그들이 있었고, 많은 도움을 받았다.<br>
블로그에 내가 실제로 도움을 받은 블로그 주소와 함께 블로그와 다르게 한 부분을 추가로 정리하기로 했다.</p>
<p></p>
<p></p>

<br>







### 1. 깃허브 블로그 댓글 기능 추가 (Utterances)
참고 : 
<a href="https://velog.io/@outstandingboy/Github-%EB%B8%94%EB%A1%9C%EA%B7%B8%EC%97%90-%EB%8C%93%EA%B8%80-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80%ED%95%98%EA%B8%B0-ft.-Utterances"> velog </a>
<br>자세하게 잘 정리되어 있다. 덕분에 쉽게 댓글 기능을 추가할 수 있었다.

❗ 만약 깃허브에서 유저 이름과 레파지토리 이름을 복사해왔다면 Repo 부분에 띄어쓰기가 되어 있는지 확인해보자. 띄어쓰기가 있으면 404 error가 뜬다.
 ````
 <!--  Utterances Comments -->
  <script src="https://utteranc.es/client.js"
        repo="user-name/blog-comments"
        issue-term="pathname"
        label="🔔 Comment"
        theme="github-light"
        crossorigin="anonymous"
        async>
  </script>
 ````
<br>

❗ 터미널없이 쉽게 하는 법
#### 1) 깃허브 블로그 레파지토리의 post.html 파일 클릭
#### 2) 파일 편집(Edit this file) 클릭
![image](https://user-images.githubusercontent.com/108778921/189338012-08e57d63-9b34-4e09-aca1-5aa8f2bfac90.png)

#### 3) 복사한 Utterances 스크립트를 원하는 위치에 붙여 넣으면 끝! 
`다른 테마의 깃허브 블로그도 아마 "{ content }" 아래에 붙여 넣으면 될 것`

<br>

### 2. 깃허브 블로그 검색엔진 등록<br>
참고 : 
<a href="http://jinyongjeong.github.io/2017/01/13/blog_make_searched/"> http://jinyongjeong.github.io/2017/01/13/blog_make_searched/ </a><br>
깔끔하게 잘 정리되어 있어 쉽게 검색 엔진에 등록할 수 있었다.

<br>
나는 구글에만 등록했는데 구글 검색 엔진 등록 방법을 좀 더 자세하게 설명하자면,

#### 1) 구글 웹마스터 도구에 접속
[https://search.google.com/search-console/](https://search.google.com/search-console/welcome) 클릭 <br>

#### 2) 깃허브 블로그 주소 입력
![image](https://user-images.githubusercontent.com/108778921/189334936-d4802c36-42e1-4ddc-a830-3c059391a303.png)<br>
깃허브 블로그 주소 URL 접두어에 입력<br>

#### 3) 소유권 확인
![image](https://user-images.githubusercontent.com/108778921/189335366-fe329bb6-7d70-44f0-b151-98a91f5bb9e4.png)<br>
HTML 파일 다운받아서 sitemap.xml 파일이 있는 공간(/root)에 업로드<br>

#### 4) Sitemap에 sitemap.xml 입력
![image](https://user-images.githubusercontent.com/108778921/189334788-e95f341e-ef10-4c1f-9a71-362088bb7b5b.png)
<br>

## 완료🙌

<br>

`+) 2022.09.11  |  네이버, 다음 검색 엔진도 등록했다. 아래의 블로그를 보고 그대로 따라하니 문제없이 등록됐다.`
<br>
참고 : <a href="https://yenarue.github.io/tip/2020/04/30/Search-SEO/">블로그</a>

<br>
