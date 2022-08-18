---
layout: post
title: "typescript APP 만들기 과정 (+ eslint, prettier 설정)"
categories:
  - React
---

# typescript APP 만들기

1. 타입스크립트 생성

`npx create-react-app "이름" --template typescript`

이름에 원하는 폴더 이름 넣고 실행 하면 프로젝트 생성 완료

```
$npm i --save react react-dom typescript
$npm i --save-dev @types/react @types/react-dom @types/node
```

> > typescript 관련 라이브러리 설치

후에 tsconfig.json 에 `"baseUrl": "./src",` 추가 >> 초기 경로 설정값(나중에 프로젝트 커지면 꼬이기떄문)

1. eslint

JavaScript 코드에서 발견된 문제 패턴을 식별하기 위한 정적 코드 분석 도구이다.

extenstion에서 설치 후 `$npm install -D eslint` , `$npx eslint --init`

typescript로 사용할꺼냐는 질문과 관련 라이브러리 설치는 필수로 y 답변 진행

```
$npm i -D eslint-config-airbnb-base # 리액트 관련 규칙 X
$npm i -D eslint-config-airbnb # 리액트 관련 규칙 O

$npm i -D eslint-plugin-react eslint-plugin-react-hooks
$npm i -D eslint-plugin-jsx-a11y eslint-plugin-import eslint-plugin-prettier eslint-config-prettier
```

- eslint-plugin-import : ES6의 import, export 구문을 지원, 필수 플러그인
- eslint-plugin-react : React 규칙이 들어있는 플러그인
- eslint-plugin-react-hooks : React Hooks 규칙이 들어있는 플러그인
- eslint-plugin-jsx-a11y : JSX요소의 접근성 규칙에 대한 정적 검사 플러그인

후에 eslintrc.js에

```
module.exports = {
  parser: '@typescript-eslint/parser',
  plugins: ['@typescript-eslint', 'prettier'],
  extends: [
    'airbnb', // or airbnb-base
    'plugin:react/recommended',
    'plugin:jsx-a11y/recommended', // 설치 한경우
    'plugin:import/errors', // 설치한 경우
    'plugin:import/warnings', // 설치한 경우
    'plugin:@typescript-eslint/recommended',
    'plugin:prettier/recommended',
  ],
  rules: {
    'linebreak-style': 0,
    'import/prefer-default-export': 0,
    'import/extensions': 0,
    'no-use-before-define': 0,
    'import/no-unresolved': 0,
    'react/react-in-jsx-scope': 0,
    'import/no-extraneous-dependencies': 0, // 테스트 또는 개발환경을 구성하는 파일에서는 devDependency 사용을 허용
    'no-shadow': 0,
    'react/prop-types': 0,
    'react/jsx-filename-extension': [
      2,
      { extensions: ['.js', '.jsx', '.ts', '.tsx'] },
    ],
    'jsx-a11y/no-noninteractive-element-interactions': 0,
    '@typescript-eslint/explicit-module-boundary-types': 0,
  },
  settings: {
    'import/resolver': {
      node: {
        extensions: ['.js', '.jsx', '.ts', '.tsx'],
      },
    },
  },
};
```

이렇게 채워줘 규칙 생성

1. prettier

extension에서 설치 후 `$npm install -D prettier`

루트 폴더에 .prettierrc 파일 생성 후

```
{
  "singleQuote": true,
  "semi": true,
  "useTabs": false,
  "tabWidth": 2,
  "trailingComma": "all",
  "printWidth": 80,
  "arrowParens": "always",
  "orderedImports": true,
  "bracketSpacing": true,
  "jsxBracketSameLine": false
}
```

> > [https://prettier.io/docs/en/options.html](https://prettier.io/docs/en/options.html)

프리티어 규칙 참고 홈페이지

참고 블로그
[[React] create-react-app & Typescript 초기 세팅 완벽 정리](https://velog.io/@junghyeonsu/React-create-react-app-Typescript-%EC%B4%88%EA%B8%B0-%EC%84%B8%ED%8C%85-%EC%99%84%EB%B2%BD-%EC%A0%95%EB%A6%AC)
