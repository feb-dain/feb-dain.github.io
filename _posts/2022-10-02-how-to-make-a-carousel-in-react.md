---
title:  "[리액트] 라이브러리로 손쉽게 스와이퍼(슬라이더) 구현하기"
layout: post
tags: React
---


여러 라이브러리 중에 나는 Slick과 Swiper를 사용했다. 개인적으로 Slick 보다 Swiper가 훨씬 더 사용하기 편했다.

## Slick 사용법

### 1. 터미널에 slick 설치

```
npm i react-slick slick-carousel
```







### 2. 사용할 파일에 import

```jsx
import Slider from "react-slick";
import "slick-carousel/slick/slick.css";
import "slick-carousel/slick/slick-theme.css";
```

### 3. 기본 형태 붙여넣기

```jsx
import Slider from "react-slick";
import "slick-carousel/slick/slick.css";
import "slick-carousel/slick/slick-theme.css";

export default function Component() {
    const settings = {
      dots: true,
      infinite: true,
      speed: 500,
      slidesToShow: 1,
      slidesToScroll: 1
    };
    
    return (
      <div>
        <h2>Title</h2>
        <Slider {...settings}>
          <div>
            슬라이더1
          </div>
          <div>
            슬라이더2
          </div>
          <div>
            슬라이더3
          </div>
          <div>
            슬라이더4
          </div>
        </Slider>
      </div>
    );
  }
```

끝! 간편하게 사용하기는 좋으나 커스텀 하려고 하니 계속 문제가 발생했다. Next 화살표는 이미지 위에 있는데 Prev 화살표는 이미지 아래에 깔려 있어 보이지 않는 등...
이 문제에 매달리기보다는 다른 라이브러리를 찾기로 했다. 왜냐하면 그게 더 빠를 것 같았고, 또 여러 라이브러리를 써보는 게 좋을 것 같았다.
그래서 찾은 게 바로 Swiper 라이브러리!

<br>
<br>

## Swiper 사용법

### 1. 터미널에 swiper 설치

```
npm i swiper
```
❗ 만약 `Module not found: Can't resolve 'swiper/react'` 오류나면 다운그레이드하기

```
npm i swiper@6.8.4
```

### 2. 사용할 파일에 import
```jsx
import { Swiper, SwiperSlide } from "swiper/react";
import SwiperCore, { Navigation } from "swiper";

import "swiper/swiper.min.css";

SwiperCore.use([Navigation]);
```

### 3. 기본 형태 붙여넣기

```jsx
function App(){
  const settings = {
        slidesOffsetBefore: 0,
        slidesOffsetAfter : 24,
        slidesPerView: 1.8,
        spaceBetween: 8,
        initialSlide: 1,
        centeredSlides: false,
  }
  
  return (
        <Swiper {...settings}>
          <SwiperSlide>
            슬라이더
          </SwiperSlide>
        </Swiper>
  );
}
```

끝! 🤗<br><br>

![image](https://user-images.githubusercontent.com/108778921/193471333-fa0efc72-370f-4ff2-9fbe-b09ddf6944df.png)

+) `이런 식으로 브레이크 포인트도 설정 가능하다.`<br>

<p>Swiper를 이용해 편하게 슬라이더를 만들었다. 영화 앱을 만들면서 Pagination은 사용하지 않았고, Navigation(화살표)은 커스텀해서 사용했다.</p>

<br>
<br>

### Swiper 화살표 커스텀하기

```jsx
function App(){
    const prevRef = useRef(null);
    const nextRef = useRef(null);

    const settings = {
        slidesOffsetBefore: 0,
        slidesOffsetAfter : 24,
        slidesPerView: 1.8,
        spaceBetween: 8,
        initialSlide: 1,
        centeredSlides: false,

        // 화살표 커스텀
        navigation: {
            prevEl: prevRef.current,
            nextEl: nextRef.current,
        },
        onBeforeInit: (swiper) => {
            swiper.params.navigation.prevEl = prevRef.current;
            swiper.params.navigation.nextEl = nextRef.current;
            swiper.navigation.update();
        },
    };
    return (
            <div className={styles.nav}>
                <button ref={prevRef}><BsFillCaretLeftSquareFill /></button>
                <button ref={nextRef}><BsFillCaretRightSquareFill /></button>
            </div>
  );
}
```

<br>

➕
<a href="https://velog.io/@sohee-k/React-TypeScript-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-Swiper-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0image-slider-library)">
Velog</a>
<br>
화살표 커스텀 할 때 위 블로그를 참고했고, 개발자 도구로 Element를 확인해가면서 원하는 디자인으로 만들었다.
스와이퍼 라이브러리를 이용하면 화살표 커스텀은 그리 어렵지 않다.

➕

[Module not found: Can't resolve 'swiper/react'](https://stackoverflow.com/questions/69202975/module-not-found-cant-resolve-swiper-react)

[[Solved] Module not found: Can't resolve 'swiper/css'](https://namespaceit.com/blog/module-not-found-cant-resolve-swipercss)


스와이퍼 오류났을 때 참고함
<br>
<br>

