# jQuery
javascript의 라이브러리

## install
http://jquery.com 에서 다운로드

## jQuery 메뉴얼
http://api.jquery.com

## jQuery 기본문법
$(엘리먼트 오브젝트 | CSS스타일 선택지), jQuery(엘리먼트)

## 제어대상을 지정하는 방법
- jQuery(selector, [context])
- jQuery(element)

### Selector
- ("__#__id") : id selector
- ("__.__class") : class selector
- ("__element__") : element selector. DOM 노드들의 태그 이름을 지칭한다.
```javascript
<div>DIV1</div>
<script>
  $("div").css("border", "9px solid red")
</script>
```
- [name__="value"__] : Attribute Equals Selector
```javascript
$("input[value="aaa"]").next().text("select!");
```
- ("__:checked__") : checked 혹은 selected 된 element만 선택
```javascript
$("input:checked").length
```
- ("__:eq(n)__") : 동일한 element 중에서 n번째 index에 위치한 element 선택
``` javascript
$("td:eg(2)").css("color", "red");
```
- ("selector1__,__ selector2__,__ selectorN") : multiple selector

## chain
jQuery의 메소드들은 반환값으로 자기자신을 리턴해야 한다.
