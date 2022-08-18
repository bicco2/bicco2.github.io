---
layout: post
title: "Swiper 라이브러리 사용해보기"
categories:
  - ETC
---

# Swiper 라이브러리 사용해보기

```tsx
import { Swiper, SwiperSlide } from "swiper/react"; // basic
import SwiperCore, { Navigation, Scrollbar, Pagination } from "swiper";
import "swiper/css"; //basic
import "swiper/css/navigation";
import "swiper/css/pagination";

SwiperCore.use([Navigation, Pagination, Scrollbar]);

const settings = {
  spaceBetween: 10,
  navigation: {},
  pagination: { clickable: true },
  scrollbar: { draggable: true, el: null },
  slidesPerView: 1,
  onSlideChange: (swiper: any) => {
    setRoomTheme(swiper.activeIndex); //테마 설정
  },
};

<Swiper {...settings} className="flex justify-center m-10">
  <SwiperSlide className="flex justify-center">
    <img src="https://i.imgur.com/EP8Qh15.png" alt="charimg" />1
  </SwiperSlide>
  <SwiperSlide className="flex justify-center">
    <img src="https://i.imgur.com/EP8Qh15.png" alt="charimg" />2
  </SwiperSlide>
  ...
</Swiper>;
```

1. 사용할 라이브러리들 import로 받아와주고 SwiperCore.use로 사용할 swiper 속성 선언
2. settings 변수 만들어서 swiper 설정값 따로 관리한다
   navigator : 화살표로 이동할 수 있는 ui생성
   pagination : 페이지 나타내는 ui 생성

<img src="https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d641e13d-9c7e-4b2b-847a-47eb90616869/Untitled.png" alt="Untitled" border="0" />

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d641e13d-9c7e-4b2b-847a-47eb90616869/Untitled.png)

       Scrollbar : 드래그로 요소 값 볼 수 있는 속성

결과물

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/92c90806-7675-448b-b41b-a54711870aae/Untitled.png)
