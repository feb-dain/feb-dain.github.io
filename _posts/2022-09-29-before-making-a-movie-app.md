---
title:  "리액트로 영화 추천 앱을 만들기 전에"
layout: post
tags: React
---

<p>
  노마드 코드 강의를 듣고, 강의와 같은 api로 영화 앱을 만들어볼까 하다가 넣을 수 있는 기능이 별로 없을 것 같다는 이유와 한국어로 만들고 싶다는 이유로 다른 영화 api를 찾기로 했다.
  어떤 api가 좋을까 검색해 보니 영화진흥위원회 오픈 API, 네이버 API, KMDb API 그리고 The movie DB API가 있었다. 사용하기 편해 보이고 내가 원하는 기능을 구현할 수 있을 것 같아
  The movie DB API로 영화 추천 앱을 만들기로 했다. 영화를 보고 싶긴 한데 무슨 영화를 보면 좋을지 모르겠을 때, 영화 선택에 도움을 주는 앱을 만들어 보고 싶었다.
</p>
<a href="https://www.themoviedb.org/">The movie DB</a>





위 사이트에 회원가입을 하고, `프로필 > 설정 > API`에 들어가 API key를 만들면 된다.<br>
"https://api.themoviedb.org/3/movie/550?api_key=(key)" 👈 (key) 부분에 개인 key를 입력하고 fetch를 사용해 api를 가져오면 끝!<br>
api를 어떻게 활용할지는 공식 사이트 설명(ex. <a href="https://developers.themoviedb.org/3/movies/get-movie-images">이미지 사용</a>)과
json 파일을 참고하면 된다. <br>

🤔 무슨 페이지를 넣을지, route는 어떻게 할 지, 디자인은 어떻게 할 지 고민이다. 투두 리스트나 캔버스 디자인은 바로 생각나서 지체없이 코딩했는데...<br>
'넷플릭스랑 비슷하지 않으면서 직관적이며 사용자가 사용하기 편한 디자인'이 아직 떠오르질 않는다. 좀 더 고민해봐야겠다. 일단 지금은 기능부터 넣자!<br>

넣고 싶은 기능은 다음과 같다.<br>

- 홈페이지
>1. 무작위 추첨 영화 1개
>2. 평점 좋은 영화들
>3. 인기 있는 영화들
>4. 장르별 영화들
>5. 검색 기능


- 서브페이지
>영화 스틸컷, 제목, 개봉 연도, 장르, 별점, 러닝 타임, 원제, 짧은 소개, 줄거리 적절하게 배치...

<br>
<br>
배우 정보나 영화 리뷰 볼 수 있는 페이지도 생각해봐야지! 


