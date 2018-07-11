# span element 클릭 금지

나의 경우 bootstrap calendar를 특정 조건에 비활성화 시켜야 하는데 span 엘리먼트에 class로 정의되어 있었다.

```css
$('span').css('pointer-events', 'none');
```

다시 클릭 허용할 경우 
```css
$('span').css('pointer-events', 'auto');
```

캘린더 모양이 비활성 모양(회색)으로 변하진 않았지만 클릭 이벤트는 발생하지 않는다.

참고 [링크](https://stackoverflow.com/questions/6657545/setting-attribute-disabled-on-a-span-element-does-not-prevent-click-events/27723966)