# CSS
## CSS 기본 문법

> **selector(선택자) { property : value; }**

```CSS
span { color : red;}
```

## style을 HTML에 적용하는 방법
1. inline
  - 세가지 방법 중 최우선 적용되는 방법
1. internal
  - header에 &lt;style&gt; 태그로 지정하기
1. external
  - 외부파일(.css)로 지정하기
  - html 내 &lt;link&gt;로 css 파일 선언

## CSS의 상속 개념
- 스타일 관련된 속성들을 정의하면 자식들까지 함께 적용된다.
- 배치와 관련된 속성은 상속을 받지 않는다. (ex: border, padding)

## 우선순위 (css specificity)
- id가 class보다 우선 시된다.
- 구체적으로 표현된 것 (element가 더 많이 선언되어 있는 것)이 높다.

## CSS selector
> HTML의 요소를 tag, id, class, html 태그 속성 등을 통해 쉽게 찾아주는 방법

- tag로 지정하기
```css
// <span></span> 이 해당됨
span { color : red; }
```
- id로 지정하기
```css
#myid { color : red; }
```
- class로 지정하기
```css
.myid { color : red; }
```
- 그룹으로 선택하기
-- 하위요소 선택
```CSS
#myid span { color: red;}
```
-- 자식요소 선택
```CSS
#myid > span { color: red; }
```

## px, em, rem
px : 고정 크기, pixel
em : 부모, 상위에서 정해진 pixel 대비 상대적인 크기를 지정할 수 있다. 지정된 요소의 폰트 크기를 기준으로 한다.
rem : html 요소의 폰트 크기를 기준으로 상대적인 크기를 지정한다.
- 크기가 변해야 하는 곳에는 되도록 rem을 쓰도록 한다.


## float, hidden
float를 주었을 때 상위 엘리먼트의 overflow 속성을 auto나 hidden으로 주어야 float 엘리먼트를 자식 엘리먼트로 인식하게 된다.
