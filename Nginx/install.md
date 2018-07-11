# nginx install

## 환경
CentOS 6.9

## 설치
1. /etc/yum.repos.d/nginx.repo 추가
```
[nginx]
name=Nginx Repository $basearch - Archive
baseurl=http://nginx.org/packages/centos/7/$basearch/
enabled=1
gpgcheck=0
```

2. yum info 확인

```
> yum info nginx
Available Packages
Name        : nginx
Arch        : x86_64
Version     : 1.12.2
Release     : 1.el6.ngx
Size        : 916 k
Repo        : nginx
Summary     : High performance web server
URL         : http://nginx.org/
License     : 2-clause BSD-like license
Description : nginx [engine x] is an HTTP and reverse proxy server, as well as
            : a mail proxy server.
```

3. nginx 저장소 서명 key import

```
> wget http://nginx.org/keys/nginx_signing.key
--2018-03-27 09:35:39--  http://nginx.org/keys/nginx_signing.key
Resolving nginx.org... 95.211.80.227, 206.251.255.63, 2001:1af8:4060:a004:21::e3, ...
Connecting to nginx.org|95.211.80.227|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1561 (1.5K) [text/plain]
Saving to: `nginx_signing.key'

100%[================================================================>] 1,561       --.-K/s   in 0s      

2018-03-27 09:35:40 (255 MB/s) - `nginx_signing.key' saved [1561/1561]

> rpm --import nginx_signing.key
```

4. nginx 설치
```
yum install nginx
```

5. 서버 기동 시 자동 시작하도록 설정
```
> chkconfig nginx on
> service nginx restart
```

## 설정 파일
/etc/nginx/

## 로그 파일
/var/log/nginx/




## 참고링크
- [RHEL/CentOS Ubuntu 에 nginx 설치](https://www.lesstif.com/pages/viewpage.action?pageId=25100304)
- [nginx: Linux packages](http://nginx.org/en/linux_packages.html)
