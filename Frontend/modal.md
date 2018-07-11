# Modal

브랜드 관리 모달 화면에서 엔터키 입력 시 모달 창이 close 되는 현상
- 하나의 텍스트 입력 필드를 가진 부트 스트랩 모달 대화 상자는 항상 Enter 키를 닫는다고 한다.
- onsubmit 에 return false를 추가하면 엔터를 쳐도 모달 창이 닫히지 않는다.

```html
<form id="modalform" onsubmit="return false">
```

참고 [링크](https://code.i-harness.com/ko/q/9eb195)
