# RegEx 정규식

## 숫자만

> /^[0-9]\*\$/

## 숫자와 하이픈

- 일정 범위 내 숫자와 하이픈만 허용

> /^[0-9-]{1,10}\$/

## 날짜 형식

- YYYY-MM-DD
  > /^(19|20)\d{2}-(0[1-9]|1[012])-(0[1-9]|[12][0-9]|3[0-1])\$/

## 시간

- HH:MM:SS
  > /^(?:2[0-3]|[01][0-9]):[0-5][0-9]:[0-5][0-9]\$/
