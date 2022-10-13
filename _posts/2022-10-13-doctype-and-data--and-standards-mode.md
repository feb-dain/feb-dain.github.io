---
title: "DOCTYPE, data- 속성, 표준모드와 호환모드"
layout: post
tags: Front-end
---

### Doctype이란?
Document type의 약자, **html이 어떤 버전으로 선언되었는지 웹 브라우저에게 알려주는 것.** <br>
이를 **선언해주지 않으면 호환모드로 작동**하는데 그러면 **크로스 브라우징 이슈가 훨씬 심해진다.**<br>
(호환모드의 경우 각 브라우저마다 문서를 나타내는 방식이 다르기 때문)<br>
요즘은 html5의 dtd(Document Type Definition)로 doctype을 선언 → `< !Doctype html >`










<br>

### 표준모드와 호환모드

**W3C가 웹 표준을 만들면서** 브라우저가 웹사이트를 제대로 표현할 수 없게 되자
**렌더링을 할 때 표준 모드(Standards mode) 또는 호환 모드(Quirks mode)로 렌더링을 할 수 있게 옵션이 제공되었다.** <br>
HTML 문서가 DOCTYPE을 선언하지 않음 → 호환 모드로 렌더링<br>
HTML 문서가 DOCTYPE을 선언 → 주어진 DOCTYPE에 맞게 표준 모드로 렌더링 <br>
**호환 모드로 렌더링을 하게 되면** 오래된 웹페이지들을 최신 버전의 브라우저에서도 깨지지 않게 하기 때문에 **각 브라우저마다 다르게 보일 수 있다.** <br>
예를 들어, IE의 경우 호환 모드에서 박스 모델(Box model)을 잘못 해석하지만, 나머지 브라우저들은 그렇지 않다.

<br>

### 데이터 속성이란? 

**DOM에 데이터를 저장할 수 있는 사용자 정의 데이터 속성.**
**data- 다음 오는 값이 데이터**가 된다.<br>
해당 사이트만의 자체 스크립트를 위한 속성 ⇒
**사용하고자 하는 용도에 적합한 속성이나 요소가 없을 때 사용하며 해당 웹페이지가 독자적으로 사용하는 값**

**장점**<br>
스크립트를 핸들링하기 위해서 의미 없는 클래스나 ID 사용을 하지 않아도 되고 
클래스가 이미 멀티클래스로 많이 사용된 경우, data 속성을 준 요소별로도 스타일 요소를 적용할 수 있다.

-<a href="https://github.com/baeharam/Must-Know-About-
    Frontend#%EC%B7%A8%EC%A4%80%EC%83%9D%EC%9D%B4-%EB%B0%98%EB%93%9C%EC%8B%9C-
    %EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EC%A7%80%EC%8B%9D%EB%93%A4">
    참고1 
  </a>,
  <a href="https://whales.tistory.com/3#:~:text=data%20%EC%86%8D%EC%84%B1%EC%9D%84%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4,%EB%A5%BC%20%EC%A0%81%EC%9A%A9%ED%95%A0%20%EC%88%98%20%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4.">참고2</a>
<br>
<br>
