---
layout: post
title: "browerRendering 과정"
categories:
  - ETC
---

# browerRendering

브라우저 렌더링 과정

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dee08bef-2bdf-4fe5-8a70-b6a4f3c3aedf/Untitled.png)

크리티컬 렌더링의 시간을 줄이면 웹페이지에 보여지는 시간이 줄어듦

레이아웃의 수치가 변경되는 렌더가 일어나면 3번 부터 다시 실행되고

색상이나 이미지가 변하는 즉, 레이아웃의 수치가 변하지 않는 변경사항은 4번부터 다시 된다 .

> > csstriggers 에서 렌더링 되는 것을 알아볼 수 있음

performance는 브라우저가 런타임에서 언제 어떤 처리를 하는지 확인하는 도구

left속성으로 애니메이션 작동하면 계속 layout이랑 다 바뀜

transform으로 작동시키면 composite만 발생함 >> 성능 향상
