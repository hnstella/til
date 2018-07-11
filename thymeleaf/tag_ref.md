# Thymeleaf tag reference

## #numbers - 수치 표현
정수값 표현에는 #numbers.formatInteger 사용
부동소수점 표현에는 #number.formatDecimal을 사용

```html
<td th:text="${#numbers.formatInteger(log.succ_cnt, 0, 'COMMA')}"></td>
```

참고
- [Thymeleaf](https://www.thymeleaf.org/apidocs/thymeleaf/2.0.15/org/thymeleaf/expression/Numbers.html)