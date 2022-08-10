---
layout: post
title: "CORS 에러"
categories:
  - ETC
---

# Web Server

- **Web Server(Nginx) : 웹서버 ,얘는 결국 보안을 위한 것임**
- 만약 쿠버네티스를 사용하게 된다면 nginx는 필요없을 것
  ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/44a3d949-c7fb-4cbf-8a51-205fcdc8277a/Untitled.png)

### Web Server(ws) 와 Web Application(was)의 차이

<aside>
❗ **WS(nginx)** : (정적 파일) 클라이언트로부터 요청을 받았을 때 요청에 맞는 정적 파일을 응답해주는 
HTTP Web Server로 활용되기도 하고,
**Reverse Proxy Server**로 활용하여 **WAS 서버의 부하를 줄일 수 있는 로드 밸런서**로 
활용되기도 합니다.

</aside>

<aside>
❗ **WAS** : 동적 파일 처리  (Web Server + CGI)
ㄴ ex : 아이디 패스워드 보내줄테니까 처리좀 해줘 >> 클라이언트 요청에 대한 처리

</aside>

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/331a56eb-f7cf-4203-afa8-29fff35472d1/Untitled.png)

**사용 이유** : WAS 의 부담을 덜어주기 위해 Node.js와 nginx를 같이 사용하면 좋다 .

```kotlin
https : 443
http : 80 (얘는 결국 443으로 우회된다.)
```

1. 빠르다
   동시 요청자의 대해서 처리 속도가 거의 비슷함
   초당 처리가 엄청 많다 .
2. 리버스 프록시(대리해주는것) \*\*\*
   인터넷과 백엔드 사이의 서버를 얘기함
   그 사이에서 서버로 보내는 것 로드 밸런싱 해줌
   동일한 요청에 대한 부담 낮춤(캐싱)
3. ssl 지원 (secure sockets layer) : 웹사이트와 브라우저 사이 or 두 서버 사이에 전송되는 데이터를 암호화하여 인터넷 연결을 보호하기위한 표준 기술
   nginx가 https의 인증서를 제공해줄 수 있다 .
   http가 ssl이나 tls의 보안을 받고 있다면 https 로 표현 된다 .
4. 관리자 사용자 구분 가능
5. 비동기 (이벤트 루프?) \*\*\*
   상당히 많은 트래픽을 처리할 수 있다.

<aside>
❗ **비동기란** ?
자바스크립트는 즉시 처리하지 못하는 이벤트들을 이벤트 루프에 모아 놓고, 
먼저 처리해야하는 이벤트를 실행한다.
콜백 함수, Promise.then (promise자체는 동기임), async await 
이렇게 크게 3가지 비동기 방식이 존재

</aside>

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/01677637-d3d6-45be-be90-355d4fa450e9/Untitled.png)

<aside>
❗ **이벤트 루프** ?
뭔가 호출되면 스택에 하나씩 저장된다.
(객체는 힙에 저장되는데 힙은 대부분 구조화되지 않은 큰 메모리임, 메세지는 큐에 저장)
이벤트 루프는 런타임 대기열에서 가장 오래된 메시지 부터 큐에서 꺼내 처리함
후에 매개변수 또는 호출로인한 새로운 스택프레임이 생성될 수 있다.
콜스택의 한계가 정해서 있음
web api로 넘어가게 되면 콜백 큐로 넘어가는데
콜백 큐에 있는 것은 콜스택이 비어있을 때 넣어

</aside>

```jsx
function foo(b) {
  let a = 10;
  return a + b + 11;
}

function bar(x) {
  let y = 3;
  return foo(x * y);
}

const baz = bar(7); // 42를 baz에 할당
```
