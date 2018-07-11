# inline scripting

controller 에서 전달된 model attribute 값을 스크립트에서 사용하려면 해당 model attribute 값은 전달받은 view 에서 inline script 로 접근해야 한다.

```javascript
<script type="text/javascript" th:inline="javascript">
    /*<![CDATA[*/

    $(document).ready(function() {
       var modelAttributeValue = [[${modelAttribute}]];
    }

    /*]]>*/
</script>
```

[참고링크](https://stackoverflow.com/questions/30398698/how-to-access-model-attribute-in-jquery)
[thymeleaf doc](https://www.thymeleaf.org/doc/tutorials/2.1/usingthymeleaf.html#script-inlining-javascript-and-dart)
