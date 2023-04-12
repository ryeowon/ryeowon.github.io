---
title: "DNS Record 4가지 유형 (A, AAAA, CNAME, NS)"
date: 2023-04-11 00:00:00
categories: [Network]
tags: [dns] # TAG names should always be lowercase
---

## DNS Record

## 1) DNS A Record

**Domain Name을 IP 주소와 매핑해주는 레코드**  
DNS 레코드 중 가장 기본적인 레코드로, A는 Address를 의미한다.  
IPv4 주소에만 사용되며, IPv6는 AAAA record를 사용한다.

| Type | Name        | Value           | TTL   |
| ---- | ----------- | --------------- | ----- |
| A    | example.com | 123.123.123.123 | 14400 |

TTL(Time To Live)는 A 레코드가 업데이트 되려면 14400초가 걸린다는 것을 의미한다.  
DNS 서버에 example.com을 요청하면 DNS 서버는 123.123.123.123를 반환한다.

## 2) DNS AAAA Record

**Domain Name를 IPv6 주소와 매핑해주는 레코드**

| Type | Name        | Value                                         | TTL   |
| ---- | ----------- | --------------------------------------------- | ----- |
| AAAA | example.com | 2001:0db8:85a3:0000 <br/> 0000:8a2e:0370:7334 | 14400 |

## 3) DNS CNAME Record

**Domain Name을 또다른 Domain Name으로 매핑해주는 레코드**

| Type  | Name             | Value       | TTL   |
| ----- | ---------------- | ----------- | ----- |
| CNAME | blog.example.com | example.com | 32600 |
| CNAME | www.example.com  | example.com | 32600 |

## 4) DNS NS Record

**해당 Domain에 권한이 있는 DNS 서버를 매핑해주는 레코드**  
NS란 nameserver(네임 서버)를 의미한다. 네임 서버란 A 레코드, CNAME 레코드 등 특정 도메인에 대한 모든 레코드를 저장하는 DNS 서버를 말한다.

| Type | Name        | Value                 | TTL   |
| ---- | ----------- | --------------------- | ----- |
| NS   | example.com | ns1.exampleserver.com | 21600 |

위의 예시에 따르면 ns1.exampleserver.com에 example.com에 대한 A 레코드를 요청할 수 있다.

<br/>

> reference  
> <https://www.cloudflare.com/learning/dns/dns-records/>{:target="\_blank"}
