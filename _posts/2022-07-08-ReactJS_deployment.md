---
title: "ReactJS 80번 포트에 배포하기"
date: 2022-07-08 00:00:00
categories: [Web, React]
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

그러나 포트 80번에서 실행하고 싶은 경우, 위와 같이 설정하면 다음과 같은 거부 메시지가 뜬다.

> Admin permissions are required to run a server on a port below 1024

1024 이하의 포트는 well-known 포트로, 대부분 특정한 프로세스에 사용되고 있기 때문에 웬만해서는 건드리지 않는게 좋다.
그럼에도 나는 80번 포트에서 실행해야 했기에 `sudo`를 이용하여 여러 시도를 해 보았지만 해결되지 않았다.

(참고로 개발 환경은 Linux이다)

## 해결 방법

그래서 찾은 방법은 프로젝트를 빌드해 배포하는 것이다.

serve 패키지가 설치되어 있지 않다면 먼저 설치해준다.

```
$ sudo install -g serve
```

그 후 `npm run build`로 최적화된 파일들을 생성해주고, `-l (포트번호)`를 이용해 원하는 포트에 배포해준다.

```
$ npm run build
$ sudo serve -l 80 -s build
```

생각해보니 배포 목적이었으면 애초에 빌드를 하고 실행하는 게 맞았다!
