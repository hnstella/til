# DATETIME 과 TIMESTAMP

## 공통점

* 년월일시초까지 모두 관리 가능 (YYYY-MM-DD HH:MM:SS)
* 소수점 6 자리까지의 초까지 저장 가능
* 자동으로 초기화 할 수 있음(Automatic Initialization and Updating)

## 차이점

* TIMESTAMP 는 time_zone 이라는 시스템 변수로 저장된 값을 기본으로 하여 날짜와 시간 정보를 입력받는다. 즉 저장되는 데이터 정보는 무조건 UTC 기반이다. 입력받은 데이터를 출력 할 때에는 time_zone 에 입력된 값을 기반으로 변환하여 처리한다.

# DATE

* 'YYYY-MM-DD' 형식으로 '1000-01-01' ~ '9999-12-31'까지만 입력 가능하다.

# 1 시간, 30 분 단위 조회하기

[여기](http://database.sarang.net/?inc=read&aid=23892&criteria=mysql&subcrit=&id=&limit=20&keyword=lock&page=8), [여기 2](https://okky.kr/article/338754) 참고함

> group by floor(minute(ch1)/5)

# sample

```
SELECT BEGINTIME, HOSTNAME, SUB_REQ_CNT FROM (
SELECT
DATE_FORMAT(BEGINTIME, '%Y-%m-%d %H:00') AS BEGINTIME
, HOSTNAM

, sum(SUB_REQ_CNT) as SUB_REQ_CNT
FROM S_MM1
WHERE
BEGINTIME BETWEEN DATE_FORMAT('2017-07-21 09:00:00', '%Y%m%d%H%i%s') AND DATE_FORMAT('2017-07-21 17:59:59', '%Y%m%d%H%i%s')) a
GROUP BY BEGINTIME
    ORDER BY HOSTNAME


SELECT BEGINTIME, HOSTNAME, SUB_REQ_CNT FROM (
SELECT
DATE_FORMAT(BEGINTIME, '%Y-%m-%d %H:00') AS BEGINTIME
, HOSTNAME
, sum(SUB_REQ_CNT) as SUB_REQ_CNT
FROM S_MM1
WHERE
BEGINTIME BETWEEN DATE_FORMAT('2017-07-21 09:00:00', '%Y%m%d%H%i%s') AND DATE_FORMAT('2017-07-21 17:59:59', '%Y%m%d%H%i%s')
GROUP BY hour(BEGINTIME))  a
    GROUP BY BEGINTIME
```

# 참고

[링크#1](http://mysqldba.tistory.com/268)
[링크#2](https://www.codeproject.com/Tips/1215635/MySQL-DATETIME-vs-TIMESTAMP)
[링크#3(mysql reference)](https://dev.mysql.com/doc/refman/5.7/en/datetime.html)
