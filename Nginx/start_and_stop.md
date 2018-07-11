# Nginx 시작/정지/재시작

## Nginx 시작
Basic Example
CentOS - `/usr/sbin/nginx`

Advanced Example
`/usr/sbin/nginx -t -c ~/mynginx.conf -g "pid /var/run/nginx.pid; worker_processes 2;"`

## 정지
`/usr/sbin/nginx -s stop`


## 참조링크
[Starting, Stopping, and Restarting NGINX](https://www.nginx.com/resources/wiki/start/topics/tutorials/commandline/)
