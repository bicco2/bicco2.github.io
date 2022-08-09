---
layout: post
title: "image_full_error "
categories:
  - Error
---

# image full

```tsx
<Box
      // display="flex"
      textAlign={"center"}
      style={{
        backgroundImage: "url(ggu2.jpg)",
        backgroundPosition: "center",
        height: "100vh",
        backgroundRepeat: "no-repeat",
        display: "flex",
        justifyContent: "center",
      }}
    >
```

이거때문에 고생 좀 했다.

backgroundImage로 Box. 즉 해당 상위 컴포에 이미 적용(public폴더에 이미지넣으면 편하다.)

backgroundPosition 으로 화면 이동시에도 center로 설정되도록 한다.

그리고 width를 100%로 화면 너비를 꽉비우고 height : 100vh로 높이를 뷰포터에 맞게 적용시킨다.

(vh 요소는 높이값의 100분의 1)
