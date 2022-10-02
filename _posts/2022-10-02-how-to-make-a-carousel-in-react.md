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

```
import Slider from "react-slick";
import "slick-carousel/slick/slick.css";
import "slick-carousel/slick/slick-theme.css";
```

### 3. 기본 형태 붙여넣기

```
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
