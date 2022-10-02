---
title:  "[리액트] 라이브러리로 손쉽게 스와이퍼(슬라이더) 구현하기"
layout: post
tags: React
---


여러 라이브러리 중에 나는 Slick과 Swiper를 사용했다. 개인적으로 Slick 보다 Swiper가 훨씬 더 사용하기 편했다.

### Slick 사용법

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
