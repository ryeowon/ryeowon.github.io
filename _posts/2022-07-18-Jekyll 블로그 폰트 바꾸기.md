---
title: "Jekyll 블로그 폰트 바꾸기"
date: 2022-07-18 00:00:00
categories: [Web, Jekyll]
tags: [web, jekyll] # TAG names should always be lowercase
---

지킬 테마를 이용해서 블로그를 만들고 나니 폰트가 너무 마음에 안 들었다 ..  
이 폰트 바꾸는 법 찾는 데만 며칠이 걸렸는데 ...!! 하고 보니 아주 간단했다.

이 방법은 내가 사용한 [Chirpy 테마](https://github.com/cotes2020/chirpy-starter){:target="\_blank"} 기준이지만, 다른 지킬 테마에도 적용할 수 있을 거라 생각한다.

## 폰트 고르기

[Google Fonts](https://fonts.google.com/?subset=korean){:target="\_blank"}에 접속해 원하는 폰트를 클릭하면 다음과 같이 스타일을 선택하는 화면이 나온다.
![Select this style](/assets/img/font1.png)
**Select this style** 버튼을 눌러 원하는 스타일을 **모두** 추가해준다.

웹 페이지 오른쪽 상단의 **View selected families** 버튼을 누르면 다음과 같은 창이 뜨는데  
![code](/assets/img/font2.png)  
**@import**를 선택한 후 style 태그 안에 있는 부분을 **복사**해주고, 아래의 **CSS rule**을 확인해둔다.

## scss 파일 찾기

블로그의 scss 파일에는 블로그 디자인과 관련된 코드들이 들어있다.  
그 중 글씨체 설정이 되어있는 부분을 찾아야 한다.

먼저 블로그에 접속해 Ctrl+Shift+C를 누르고(Windows 기준), 바꾸고 싶은 글자를 클릭한다.
그러면 해당 요소의 css를 확인할 수 있는데, 그 중 **font-family** 속성을 찾고 해당 코드가 있는 **파일 이름과 라인 넘버를 확인**한다.
![font-family](/assets/img/font3.png)

그 후 해당 파일을 찾아야 하는데, 보통 그 파일은 \_sass 폴더 내에 있을 것이다.  
나의 경우 [Chirpy Starter](https://github.com/cotes2020/chirpy-starter){:target="\_blank"}를 사용하여 \_sass 폴더가 없어서 많이 헤맸는데, [Chirpy Theme](https://github.com/cotes2020/jekyll-theme-chirpy)에서 그 폴더만 복사하여 사용하니 해결됐다.

## 폰트 수정하기

찾은 scss 파일 맨 위에에 복사한 코드를 넣어준다.

```
//예시
@import url('https://fonts.googleapis.com/css2?family=Gowun+Dodum&display=swap');
```

그 후, 위에서 찾은 라인 넘버를 따라가 font-family 요소를 찾고, 확인했던 CSS rule로 바꿔 준다.  
(위의 예시의 경우 commons.scss 파일의 32번째 줄)

```
body {
    ...
    font-family: 'Gowun Dodum';
    ...
}
```

끝!!
