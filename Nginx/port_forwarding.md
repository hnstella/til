# Port Forwarding

nginx에서 80포트로 들어오는 HTTP 요청에 대해 특정 포트(ex:8080)로 포워딩해주도록 설정한다.

nginx.conf
- server 설정은 conf.d에 별도 파일로 생성하고 include 시킨다.
```
http {
  .....
  include /etc/nginx/conf.d/proxy.conf;
}
```

conf.d/proxy.conf
```
server {
    ...
    location / {
        ...
        proxy_set_header    Host $host;
        proxy_set_header    X-Real-IP   $remote_addr;
        proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass  http://127.0.0.1:8080;
    }
    ...
  }
```
