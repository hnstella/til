# Props

## props 란?

상위 컴포넌트에서 하위 컴포넌트로 데이터를 전달할 때 사용하는 속성

## 사용 방법

1.  하위 컴포넌트의 속성에 props 정의

```javascript
Vue.component('child-component', {
  props: ['props 속성이름']
});
```

2.  상위 컴포넌트의 Html 코드에 등록된 child-component 태그에 v-bind 속성 추가

```html
<child-component v-bind:props 속성이름="상위 컴포넌트의 데이터 속성"></child-component>
```

## 컴포넌트 간의 관계

전역 컴포넌트 등록 시 부모, 즉 상위 컴포넌트는 자연스럽게 뷰 인스턴스가 된다.

상위 컴포넌트는 props 를 통해 하위 컴포넌트로 데이터를 전달하고하위 컴포넌트는 event 를 발생시켜 상위 컴포넌트로 신호를 보내거나 이벤트 버스를 통해 데이터를 전달시킬 수 있다.

## props 잘 사용하기

props 를 잘 정의하면 API 가 된다.
예측 가능한 API 를 사용하면 컴포넌트는 항상 잘 작동할 것이다.(방어적 프로그래밍)

* props 에 기본 값을 사용하자
* 값을 validate 하기 위해 _type_ 옵션을 사용하자ㅍ
* 중복된 props 가 있는지 확인하자

## Links

[컴포넌트 props 를 원시 자료형으로 사용하기](http://vuejs.kr/jekyll/update/2017/03/13/vuejs-component-style-guide/#%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-props%EB%A5%BC-%EC%9B%90%EC%8B%9C-%EC%9E%90%EB%A3%8C%ED%98%95%EC%9C%BC%EB%A1%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)

[Intro to Vue.js: Components, Props, and Slots](https://css-tricks.com/intro-to-vue-2-components-props-slots/)
