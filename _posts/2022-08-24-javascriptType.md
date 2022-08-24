---
layout: post
title: "javascript의 타입"
categories:
  - ETC
---

javascript의 타입

asyn는 병렬로 html 파싱하다가 fetching 하고 fetching이 끝나면 executing가 됨

> > 단점은 js 파일안에 html dom 요소를 사용하는 코드가 있으면 오류가 발생해 위험할 수 있음
> > 그리고 html parsing이 병렬처리를 위해 중간중간 멈춘다.

script 태크를 head 태크 안에

<script defer src = “test.js”></script>

로 사용하는게 제일 효율적이다.
asyn는 html 파싱 도중 멈추지만 defer은 js를 다운로드(fetching)만 해놓음 그리고 html parsing이 끝나면 그때 executing 함
fetching이 내가 설정한 순서대로 이루어짐 (안전하다.)

var는 호이스팅을 통해 어디에 선언되는가에 상관없이 실행 즉시 상단으로 끌어올리게 된다
function도 호이스팅이 된다.
심지어 스코프(블록)내에서 선언해도 스코프 밖에서 가져다 쓸 수 있음 >> 위험 부담이 너무 크다 .

> > let은 es6에서 추가된 변수명으로 위의 var 변수의 단점을 보완한 것으로 보면 된다 . 읽고 쓰기 가능
> > const는 읽기만 가능

자바스크립트는 런타임 언어 >> dynamic type으로 js가 변수내의 값을 유추해 알아서 해줌, 편할 수 있지만 개발할때 이런 에러를 런타임 에러로 분류해버려 타입 에러가 났을 때 디버깅이 어렵다는 단점을 가지고 있어 typescript가 등장함

js types

1. number (infinity ex.1 / 0)
2. string
3. boolean (false : 0, null , undefined, NaN, ‘’)
4. null(nothing), undefined(선언은 됐지만 뭐가 할당된지 모를때 따로 할당도 가능)
5. symbol (고유한 식별자를 만들 수 있다.) Symbol.for(‘’) > 동일한 심볼 , symbol.description으로 벨류 값 사용 가능
6. object(const bicco = {name : ‘hobyeong’ , age : 20 ) bicco 자체는 const라 포인터가 잠겨 다른 오브젝트로 할당이 불가하지만 내부의 변수들은 변경 가능, 그리고 let은 value가 저장되는 반면 , object는 value를 가르키는 레퍼런스를 저장한다.

note code

```tsx
// 2. Variable, rw(read/write)
// let (added in ES6)
let globalName = "global name";
{
  let name = "ellie";
  console.log(name);
  name = "hello";
  console.log(name);
  console.log(globalName);
}
console.log(name);
console.log(globalName);

// var (don't ever use this!)
// var hoisting (move declaration from bottom to top)
// has no block scope
{
  age = 4;
  var age;
}
console.log(age);

// 3. Constant, r(read only)
// use const whenever possible.
// only use let if variable needs to change.
const daysInWeek = 7;
const maxNumber = 5;

// Note!
// Immutable data types: premitive types, frozen objects (i.e. object.freeze())
// Mutable data types: all objects by default are mutable in JS
// favor immutable data type always for a few reasons:
//  - security
//  - thread safety
//  - reduce human mistakes

// 4. Variable types
// primitive, single item: number, string, boolean, null, undefined, symbol
// object, box container
// function, first-class function

// number
const count = 17; // integer
const size = 17.1; // decimal number
console.log(`value: ${count}, type: ${typeof count}`);
console.log(`value: ${size}, type: ${typeof size}`);

// number - speicla numeric values: infinity, -infinity, NaN
const infinity = 1 / 0;
const negativeInfinity = -1 / 0;
const nAn = "not a number" / 2;
console.log(infinity);
console.log(negativeInfinity);
console.log(nAn);

// bigInt (fairly new, don't use it yet)
const bigInt = 1234567890123456789012345678901234567890n; // over (-2**53) ~ 2*53)
console.log(`value: ${bigInt}, type: ${typeof bigInt}`);

// string
const char = "c";
const brendan = "brendan";
const greeting = "hello " + brendan;
console.log(`value: ${greeting}, type: ${typeof greeting}`);
const helloBob = `hi ${brendan}!`; //template literals (string)
console.log(`value: ${helloBob}, type: ${typeof helloBob}`);
console.log("value: " + helloBob + " type: " + typeof helloBob);

// boolean
// false: 0, null, undefined, NaN, ''
// true: any other value
const canRead = true;
const test = 3 < 1; // false
console.log(`value: ${canRead}, type: ${typeof canRead}`);
console.log(`value: ${test}, type: ${typeof test}`);

// null
let nothing = null;
console.log(`value: ${nothing}, type: ${typeof nothing}`);

// undefined
let x;
console.log(`value: ${x}, type: ${typeof x}`);

// symbol, create unique identifiers for objects
const symbol1 = Symbol("id");
const symbol2 = Symbol("id");
console.log(symbol1 === symbol2);
const gSymbol1 = Symbol.for("id");
const gSymbol2 = Symbol.for("id");
console.log(gSymbol1 === gSymbol2); // true
console.log(`value: ${symbol1.description}, type: ${typeof symbol1}`);

// object, real-life object, data structure
const ellie = { name: "ellie", age: 20 };
ellie.age = 21;

// 5. Dynamic typing: dynamically typed language
let text = "hello";
console.log(text.charAt(0)); //h
console.log(`value: ${text}, type: ${typeof text}`);
text = 1;
console.log(`value: ${text}, type: ${typeof text}`);
text = "7" + 5;
console.log(`value: ${text}, type: ${typeof text}`);
text = "8" / "2";
console.log(`value: ${text}, type: ${typeof text}`);
console.log(text.charAt(0));
```
