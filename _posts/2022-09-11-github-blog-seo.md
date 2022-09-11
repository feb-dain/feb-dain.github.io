---
title:  "깃허브 블로그 검색 엔진 최적화(SEO)하기"
layout: post
tags: GitHub-Blog
---

<p>
  <b>SEO란?</b> 검색 엔진 최적화(search engine optimization)의 준말로 <br>
  구글이나 네이버, 다음 등과 같은 검색 엔진에서 검색이 잘 되도록 하는 것을 말한다. <br>
  네이버 검색 엔진에 깃허브 블로그를 등록하다가 '웹 페이지 최적화'를 발견했다. <br>
  '검색 엔진이 요청한 페이지 콘텐츠를 잘 해석할 수 있는지'를 진단할 수 있는 좋은 기능이다.
</p>
<a href="https://searchadvisor.naver.com/console/board">네이버 웹마스터 도구</a>에 들어가서

![image](https://user-images.githubusercontent.com/108778921/189526397-5d54f6b4-0c61-49b8-a689-470ffe5507d8.png)


<p></p>






사이트 등록(링크 입력 후 Enter)하고<br> 
하단의 `사이트 목록의 링크` 클릭 -> `검증` -> `웹 페이지 최적화`에서 <span style="color:green">확인</span> 버튼을 누르면<br><br>

![image](https://user-images.githubusercontent.com/108778921/189525777-5dbc6074-f1df-4b33-80b7-ccda01a40018.png)

이렇게 항목이 뜬다.<br>
  
나는 <b>페이지 설명, Open Graph 제목, Open Graph 설명</b>에 ❌ 표시가 떴었는데, 이럴 경우 간단하게 <head> 태그 아래에 코드 3줄만 추가해주면 된다.

![image](https://user-images.githubusercontent.com/108778921/189527071-7f9b8207-1668-4f19-a6e7-0dd9a2d20138.png)

```  
<meta name="description" content="{% if page.excerpt %}{{ page.excerpt | strip_html | strip_newlines | truncate: 160 }}{% else %}{{ site.description }}{% endif %}">
<meta property="og:title" content="{% if page.title %}{{ page.title | escape }}{% else %}{{ site.title | escape }}{% endif %}">
<meta property="og:description" content="{% if page.excerpt %}{{ page.excerpt | strip_html | strip_newlines | truncate: 160 }}{% else %}{{ site.description }}{% endif %}">
```  
<br>
 
