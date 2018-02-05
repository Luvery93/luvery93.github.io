---
layout: post
title: iptables를 사용한 방화벽 설정
date: 2018-02-05 17:10 +0900
categories: [Development]
comments: true
---

* 아래 명령어를 스크립트로 작성하여 기본 방화벽을 설정할 수 있습니다. (우분투 16.04)

```
#!/bin/bash
# iptalbes 초기화
iptables -F

# TCP PORT 22 를 열어 SSH 접속을 가능 하도록 설정
iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT

# 기본 정책 설정
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# localhost 접속 허용
iptables -A INPUT -i lo -j ACCEPT

# established and related 접속 허용
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# DNS TCP 53 / UDP 53
iptables -A INPUT -p tcp --dport 53 -j ACCEPT
iptables -A INPUT -p udp --dport 53 -j ACCEPT

# FTP passive mode
iptables -A INPUT -p tcp --dport 21 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 21 -j ACCEPT
iptables -A INPUT -p tcp --dport 1024:65535 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 1024:65535 -j ACCEPT

# 80, 443 포트 개방
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# 설정 내용 저장
service iptables save

# 설정 내용 출력
iptables -nL
```