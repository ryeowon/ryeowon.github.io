---
title: "ReactJS 80번 포트에 배포하기"
date: 2022-07-08 00:00:00
categories: [Web, ReactJS]
tags: [web, react] # TAG names should always be lowercase
---

ReactJS를 `npm run start`로 실행하면 기본적으로 port 3000을 사용한다.  
이 포트를 바꾸고 싶을 때는 운영체제에 따라 다음과 같이 설정하고 `npm run start`로 실행하면 된다.

```
//package.json (Linux)
...
"scripts": {
    "start": "export PORT=1234 && react-scripts start",
    ...
}
...
```

```
//package.json (Windows)
...
"scripts": {
    "start": "set PORT=1234 && react-scripts start",
    ...
}
...
```

그러나 포트 80번에서 실행하고 싶은 경우, 위와 같이 설정하면 다음과 같은 메시지가 뜨며 거부당한다...

> Admin permissions are required to run a server on a port below 1024

1024보다 작은 포트에서 실행하기 위해서는 admin permission이 있어야 한다는 것인데, 나의 경우 아무리 `sudo`를 이용해도 해결되지 않았다.

(참고로 개발 환경은 Linux이다)

## 해결 방법

그래서 찾은 방법은 `npm run build`를 이용해 배포하는 것이다.

```
$ npm run build
$ sudo serve -l 80 -s build
```

먼저, `npm run build`로 최적화된 파일들을 생성해주고, `-l (포트번호)`를 이용해 원하는 포트에 배포해준다.
