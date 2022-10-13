---
title: "시맨틱 마크업이란?"
layout: post
tags: Front-end
---

'시맨틱 태그'는 의미가 있는 태그로, 보는 사람이 태그의 이름만 보고도 어떤 태그인지 알 수 있게 한다.
이러한 **시맨틱 태그를 적절하게 사용해 문서를 작성하는 것을 시맨틱 마크업**이라고 한다.










시맨틱 마크업 사용 예시는 다음과 같다.
- 헤더/푸터에 `<header>` 와 `<footer>` 사용
- 메인 컨텐츠에 `<main>` 과 `<section>` 사용
- 독립적인 컨텐츠에 `<article>` 사용
- 최상위 제목으로 `<h1>` 사용
- 순서가 없는 목록으로 `<ul>` 과 `<li>` 사용
- 내비게이션에 `<nav>` 사용

또 CSS 스타일을 명시하는 태그를 사용하지 않는 것 또한 시맨틱 마크업의 한 종류이다.
**태그가 가지는 의미 자체가 스타일이라면 마크업 자체가 스타일을 갖는 것이기 때문에 시맨틱 마크업에 적합하지 않다.**
동일한 효과를 부여하는 < strong > 과 < b > 태그로 예를 들어보자.<br>
둘 다 글자색을 진하게 하지만 < b > 태그의 경우, 그 자체가 "bold" 의 약자이기 때문에 태그 자체가 스타일을 가진다고 할 수 있다.
하지만 < strong > 태그의 경우, "그 안의 내용이 다른 내용보다 더 강조되어야 한다"라는 의미를 가지기 때문에 시맨틱 마크업에 더 적합하다.

### 장점

- **검색엔진 최적화(SEO)에 유리** : 검색엔진이 시맨틱 태그를 중요한 키워드로 간주한다.
- **웹 접근성** : 시각장애가 있는 사용자가 그 의미를 훨씬 잘 파악할 수 있다.
- **좋은 가독성** : 단순하게 `div` , `span`으로 둘러싸인 코드보다 읽기 편하다.

-<a href="https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/html/semantic.md">참고</a><br>

<br>
<br>
시맨틱 마크업을 완벽하게 쓰긴 어렵지만, 지키도록 노력하는 것이 좋다!<br>
내가 시맨틱 마크업을 잘 지켰는지 확인하고 싶다면? <br>
<a href="https://validator.kldp.org/"> 마크업 검사 </a><br>
☝ 위의 사이트에 검사하고 싶은 사이트의 url을 붙여 넣거나 파일을 업로드하거나 코드를 붙여넣기하면 된다. 

<br>
<br>