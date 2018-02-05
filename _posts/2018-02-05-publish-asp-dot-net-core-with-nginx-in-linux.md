---
layout: post
title: "Linux Nginx를 통한 asp.net core 웹앱 배포"
date: 2018-02-05 17:13 +0900
categories: [Development]
comments: true
---

* Ubuntu에 .NET Core dev를 설치합니다. 우분투 16.04기준이며 다른 플랫폼은 [여기](https://www.microsoft.com/net/core#linuxubuntu)에서 다운받습니다.

```
# sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
# apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893
# apt-get update
```

* Nginx를 설치합니다.

```
# apt-get install nginx
# service nginx start
```

* Nginx 설정 파일을 추가합니다.

```
# vi /etc/nginx/conf.d/prj.conf

server {
        listen 80;
        server_name prj.domain.com
        client_max_body_size 524288000;
        location / {
                root /prj/www/publish;
                index index.html;
                access_log /prj/www/log/access.log;
                error_log /prj/www/log/error.log;
                proxy_pass http://localhost:5000;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Conneciton keep-alive;
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
        }
}

# nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
# nginx -s reload
```

* Service 파일을 생성하고 등록, 실행, 상태 확인을 진행할 수 있습니다.

```
# vi /etc/systemd/sytem/asp.net-prj.service
[Unit]
Description=PRJ .NET Web API Application running on Ubuntu

[Service]
WorkingDirectory=/prj/www/publish
ExecStart=/usr/bin/dotnet /prj/www/publish/XXX.dll
Restart=always
Restartec=10
SyslogIdentifier=prj-web
User=www-data
Environment=ASPNETCORE_ENVIRONMENT=Production

[Install]
WantedBy=multi-user.target

# systemctl enable asp.net-prj.service
# systemctl start asp.net-prj.service
# systemctl status asp.net-prj.service
```