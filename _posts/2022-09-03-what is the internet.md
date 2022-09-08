---
title: "인터넷(Internet)이란?"
date: 2022-09-03 00:00:00
categories: [Network]
tags: [network, internet] # TAG names should always be lowercase
---

## 인터넷이란?

인터넷은 전 세계적으로 연결되어있는 **컴퓨터 네트워크 통신망**을 말한다.

## 인터넷의 시작

인터넷의 원형은 **ARPANET(아파넷)**으로 알려져 있는데, 이는 Vint Cerf(빈트 서프)와 Bob Kahn(밥 칸)이 설계한 세계 최초의 패킷교환방식을 이용한 네트워크이다. 냉전 시대였던 당시에는 **핵공격에도 살아남을 수 있는 통신 시스템**이 필요했다. 컴퓨터 네트워크 개발의 선구자인 Paul Baran(폴 바란)은 **정보를 블록(패킷)으로 쪼개어 분산된 네트워크를 통해 가능한 빨리 모든 방향으로 보내자**는 아이디어를 냈다.

<img src="/assets/img/baran_networks.png" alt="centralized and distributed network">

그림에서 알 수 있듯이 중앙 집중식(Centralized) 네트워크를 이용하면 중앙 서버에 핵공격을 당했을 때 네트워크가 완전히 마비된다. 따라서 분산(Distributed) 네트워크를 이용하여 공격 받지 않은 부분을 통해서라도 통신할 수 있도록 하자는 것이다. 이 아이디어를 바탕으로 Distributed Packet-Switched Network인 ARPANET이 개발되었다.

- packet-switched network: 데이터가 패킷(데이터 조각) 단위로 나뉘어 전송되는 네트워크

## 분산된 네트워크

인터넷은 **독립적으로 운영되는 네트워크**로 구성되어 있다. 이는 패킷이 어떤 경로를 거쳐갈지, 누가 누구와 통신할지 결정하는 중앙 통제가 없는 **완전히 분산된 시스템**을 말한다. 이러한 시스템의 인터넷은 우리가 전 세계의 어떤 장치와도 소통할 수 있도록 만든다.  
<br/>

> reference  
> <https://www.youtube.com/watch?v=Dxcc6ycZ73M>{:target="\_blank"}  
> <https://netspecific.net/en/netspecific/network-curation>{:target="\_blank"}
