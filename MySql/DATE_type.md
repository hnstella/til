# DATE type

## 일별 조회하기

WHERE s_date BETWEEN '2018-03-08' AND '2018-03-09'

## 월별 조회하기

SELECT DATE_FORMAT( s_date, '%Y-%m' ) AS DATE, sender_mdn, req_sms FROM STAT_ALIAS
where DATE_FORMAT(s_date, '%Y-%m') BETWEEN '2016-10' AND '2016-10';
