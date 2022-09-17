---
title: "iframe 삽입이 안 되는 이유"
date: 2022-09-17 00:00:00
categories: [Security, Web Security]
tags: [iframe, x-frame-options] # TAG names should always be lowercase
---

HTML `<iframe>` 태그는 HTML 문서에 다른 문서를 삽입할 때 사용한다.  
그러나 Google, Gmail, Naver 등의 페이지를 삽입하려고 하는 경우 아래처럼 연결을 허용하지 않는다.

<img src="/assets/img/iframe.png" alt="google iframe"/>

## iframe 오류 원인

https://www.google.com을 iframe으로 삽입하고자 할 때, 크롬 개발자 도구의 Console 창을 보면 `Refused to display 'https://www.google.com/' in a frame because it set 'X-Frame-Options' to 'sameorigin'.`라는 메시지를 확인할 수 있다.  
  

즉, 구글은 **origin이 같은 페이지**(도메인 이름, 포트 번호, 프로토콜이 같은 페이지)에서만 iframe으로 구글을 삽입할 수 있도록 하고 있다. 그 이유는 클릭재킹과 같은 공격들을 막기 위함이다. 따라서 localhost나 다른 개인 페이지에서 iframe을 이용해 www.google.com을 삽입할 수 없다.

> X-Frame-Options: <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options>{:target="_blank"}

## X-Frame-Options 확인 방법

X-Frame-Options는 **HTTP Response Headers**에 담겨 있다.  

개발자 도구에서 Network를 선택하여 페이지를 다시 로드하고, iframe으로 삽입하고자 했던 페이지를 선택하면 Response Headers를 볼 수 있다. 아래는 www.google.com을 삽입 시도했을 때의 response headers이고, x-frames-options가 SAMEORIGIN으로 설정되어 있는 것을 볼 수 있다.

<img src="/assets/img/header.png" alt="response header">

이 설정이 DENY로 되어 있는 경우에도 해당 페이지를 iframe으로 삽입할 수 없다.

## 해결 방안

iframe 대신 웹사이트에서 제공하는 **API**를 사용하자.  

  
구글의 경우 https://www.google.com 대신 https://www.google.com/webhp?igu=1 를 사용하면 삽입이 되긴 한다.  
이 페이지는 X-Frame-Options가 존재하지 않는다.