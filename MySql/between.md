# BETWEEN

[참고](http://ourcstory.tistory.com/102)

## 시간 조건 걸기
timestamp에 between <time> and <time> 조건으로 검색하기

```
SELECT count(*) FROM
WHERE timestamp BETWEEN '2018-03-08 00:00:00' AND '2018-03-09 23:59:59'
GROUP BY user_id;
```
