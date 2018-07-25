# Apache

기본 위치 : /usr/sbin
설정 파일 : /etc/httpd/conf/httpd.conf
로그 파일 : /var/log/httpd/access_log

## 설치 위치
```
> service httpd status
httpd is stopped
> which httpd
/usr/sbin/httpd
> /usr/sbin/httpd -v
```

## 기본 명령어 
### 우분투 - 서비스명:apache2
- 상태 확인 : `systemctl status apache2`
- 아파치 시작 : `systemctl start apache2`
- 아파치 정지 : `systemctl stop apache2`
- 아파치 재시작 : `systemctl restart apache2`
- 아파치 리로드 : `systemctl reload apache2`

### CentOS - 서비스명:httpd
- 상태 확인 : `systemctl status httpd`
- 아파치 시작 : `systemctl start httpd`
- 아파치 정지 : `systemctl stop httpd`
- 아파치 재시작 : `systemctl restart httpd`
- 아파치 리로드 : `systemctl reload httpd`


# 참고링크
- [제타위키](https://zetawiki.com/wiki/%EC%95%84%ED%8C%8C%EC%B9%98_%EC%9B%B9%EC%84%9C%EB%B2%84)
- [centOS](https://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-apache-startstop.html)