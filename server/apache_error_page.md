# 아파치 에러 페이지 설정하기

## 아파치 버전 확인

```bash
[dooeul@hsweb www]$ /usr/sbin/httpd -v
Server version: Apache/2.2.3
Server built:   Jul 18 2016 10:51:39
```

## httpd.conf

- 경로(linux) : /etc/httpd/conf

```
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 402 http://www.example.com/subscription_info.html
```

- 텍스트 표시 : 입력된 텍스트 표시
- 서버 내부 전환 : 서버 내 만들어놓은 페이지로 전환
- 외부 경로 전환 : 외부 페이지로 전환

## 서버 내부 전환

Root path 로 인식하는 DocumentRoot 를 확인해야 한다.

centOs 5.6 의 경우 /var/www (이게 설명마다 기본 root path 가 다르다..)

- RHEL 과 CentOs 의 경우 따옴표를 넣어주어야 정상적으로 작동한다고 한다.

```
DocumentRoot "/var/www"
ErrorDocument 404 "/errorpage/error404.html"
ErrorDocument 500 "/errorpage/error500.html"
```

### 서버에서 찾아본 경로

```
[dooeul@hsweb conf]$ cat /etc/issue.net
CentOS release 5.6 (Final)
Kernel \r on an \m

[dooeul@hsweb conf]$ cd /var/www
[dooeul@hsweb www]$ ll
합계 20
drwxr-xr-x  2 root root 4096  7월 19  2016 cgi-bin
drwxr-xr-x  3 root root 4096  1월  4  2017 error
drwxr-xr-x  2 root root 4096  7월 19  2016 html
drwxr-xr-x  3 root root 4096  1월  4  2017 icons
drwxr-xr-x 14 root root 4096  1월  4  2017 manual
```

## 참고링크

- [Apache ErrorDocument 설정 따라하기](https://hello-nanam.tistory.com/56)
- [How to Change Default Apache 'DocumentRoot' Directory in Linux](https://www.tecmint.com/change-root-directory-of-apache-web-server/)
