---
layout: post
title: "dependencies, devDependencies 차이"
categories:
  - ETC
---

# dependencies, devDependencies 차이

dependencies 는 일반적인 **npm install 라이브러리명**을 통해서

devDependencies 는 **npm install 라이브러리명 --save-dev** 혹은 **npm install 라이브러리명 -D** 로 설치하게 됩니다.

dependencies 에는 애플리케이션 동작과 연관된,

devDependencies 에는 애플리케이션 동작과 직접적인 연관은 없지만, 이름 그대로 개발할 때 필요한 라이브러리를 설치하시면 됩니다.

이렇게 구분해주는 이유는 결국 배포할 때 어떤 라이브러리가 포함되냐

dependencies 에 설치된 라이브러리는 배포할 때 포함되지만

devDependencies 에 설치된 라이브러리는 개발할 때 필요한 라이브러리기 때문에 배포할 때 포함되지는 않습니다

이렇게 잘 구분을 해서 설치해줘야 빌드시간도 줄이고, 배포할 때 불필요한 라이브러리를 포함시키지 않아도 된다.
