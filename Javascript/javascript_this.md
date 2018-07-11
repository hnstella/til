this
====

javascript에서 this는 함수의 현재 실행 문맥
 - 함수 실행 : alert('Hello World!')
 - 메소드 실행 : console.log('Hello World') 
 - 생성자 실행 : new RegExp('\d') 
 - 간접 실행 : alert.call(undefined, 'Hello World!') 
 
 4가지 함수 실행 타입에 따라 다른 문맥을 가진다.


함수 실행
---------

함수 실행에서의 this는 전역 객체
```javascript
function nonStrictSum(a, b) {
  // 비 엄격 모드
  console.log(this === window); // => true
  return a + b;
}
function strictSum(a, b) {
  'use strict';
  // 엄격 모드
  console.log(this === undefined); // => true
  return a + b;
}
// nonStrictSum() 함수는 비 엄격 모드로 실행
// nonStrictSum()에서의 this는 window 객체
nonStrictSum(5, 6); // => 11
// strictSum() 함수는 엄격 모드로 실행
// strictSum()에서의 this는 undefined
strictSum(8, 12); // => 20
```

메소드 실행
-----------

this는 메소드 실행에서 메소드를 소유하고 있는 객체 자신

생성자 실행
-----------

생성자 실행에서의 this는 새롭게 만들어진 객체이다.

[참고 링크](http://webframeworks.kr/tutorials/translate/explanation-of-this-in-javascript-1/)
---------------------------------------------------------------------------------------------
