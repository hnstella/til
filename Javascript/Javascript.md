## Javascript

[생활코딩 자바스크립트 언어 기본][https://www.inflearn.com/course-status-2/]

브라우저를 제어하기 위한 프로그래밍 언어

### 최근 동향
- 탈 브라우저
- 탈 웹 (ex: google apps script)

### 함수 선언식(Function Declarations)과 함수 표현식(Function Expressions)
__함수 선언식__
```javascript
function someName() {

}
someName();
```

__함수 표현식__
```javascript
  var name = function() {

  };

  name();
```

- 함수 선언식은 호이스팅에 영향을 받지만 함수 표현식은 호이스팅에 영향을 받지 않는다.

### 호이스팅(hoisting)
[참고링크][http://insanehong.kr/post/javascript-function/]

> 인터프리터가 자바 스크립트 코드를 해석함에 있어 Global 영역의 선언된 코드블럭을 최상의 Scope로 끌어올리는 것

즉 선언문은 항시 자바 스크립트 엔진 구동 시 가장 최우선으로 해석한다.
그리고 __statement는 호이스팅되지만 할당은 호이스팅되지 않는다.__
