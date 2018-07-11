# Thymeleaf 연산자 사용하기

## switch문

```html
<td th:switch="${senderMdn.status}">
    <span th:case="0">승인대기</span>
    <span th:case="1">사용</span>
    <span th:case="2">미사용</span>
</td>
```

## if / else 문
```html
<td th:if="${data.buyTime} != 0" th:text="${ddd.format(data.buyTime)}"></td>
<td th:unless="${data.buyTime} !=0">0</td>
```

## 삼항 연산자
```html
<td th:text="${data.buyTime} ? ${customformat(data.buyTime)} : '0'" ></td>
```

[참고 출처](http://firstboos.tistory.com/entry/Thymeleaf-%EC%97%90%EC%84%9C-%EC%9E%90%EC%A3%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EC%98%88%EC%A0%9C)