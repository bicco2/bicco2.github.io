---
layout: post
title: "axios_send_data_error"
categories:
  - Error
---

# Axios Send Error

**axios post 에서 받아오는 파라미터가 다른 변수에 할당해줘도 다시 초기화 되는 문제 발생**

## 이유 :

console.log()가 순서에 안맞게 실행되는 것도 문제가 될 수 있고 아마 async await의 사이클 순서와 관련된거 같다 .

비동기 처리로 처리할 수 있는 것들 먼저 처리하고 그 후에 데이터를 넘겨주기 때문에 데이터가 제대로 안넘어 가는 문제 발생

## 해결책 :

async await 비동기 처리를 할 때는 그 안에서 아예 처리하는게 편해보인다 .

이게 생명주기가 어떻게 돌아가는지 복잡하기 때문에 .
