---
layout: post
title: "Peer Dependencies"
categories:
  - Error
---

### Peer Dependencies

**Peer Dependencies**

> 실제로 패키지에서 직접 require(import) 하지는 않더라도 호환성이 필요한 경우 명시한다.

무슨 말인지 어려우니까 예를 들어보자.

`my-app` 에서 사용하기 위한 React 기반의 컴포넌트 라이브러리인 `my-ui-library`를 개발한다고 가정하자. 이 때, UI Library 에서는 `react 17.0.0` 버전을 peer dependancy로 두고 있다.

`my-ui-library`는 `react`컴포넌트의 라이브러리이기 때문에, 이 라이브러리를 사용하게 될 프로젝트에서는 `react`를 의존할 수 밖에 없다. 이러한 경우 peer dependencies를 사용한다.

무슨 말인지 여전히 어렵다. 최대한 간단히 말하자면 아래와 같다.

- -force를 하면 package-lock.json에 몇가지의 다른 의존 버전들을 추가한다.
- -legacy를 하면 peerDependency가 맞지 않아도 일단 설치한다.

**--legacy-peer-deps**
는 npm 4 ~ 6버전 때처럼 peerDependencies를 자동으로 설치하지 않도록 설정하는 것이고, **--force**
는 충돌이 일어난 peerDependecies를 강제로 설치하도록 설정하는 것이다.
