# HTML 코드 작성규칙

## 기본 규칙 {#html-1-1}

* DTD를 제외한 모든 요소와 애트리뷰트는 소문자로 작성합니다
* 애트리뷰트 값은 큰따옴표\(""\)로 묶습니다.
* 아이디와 클래스의 속성 값은 숫자, 대문자, 특수문자로 시작할 수 없습니다.
* 애트리뷰트의 속성의 값은 숫자, 특수문자로 시작할 수 없으며, 대문자로는 시작할 수 있습니다.

## 아이디 {#html-1-2}

아이디는 _**소문자 카멜 표기법**_ 을 사용합니다. 스타일 지정을 위해 사용하지 않으며, DOM 조작을 위해 사용해야 합니다.

> 주의 사항: 숫자, 대문자, 특수문자로 시작할 수 없습니다.

```javascript
<div id="headerMenu">
  ...
</div>

<div id="layerPop-1">
 ...
</div>
```

## 클래스

아이디와 시각적 구분을 위해 _**하이픈 표기법**_ 을 사용합니다.

이미 수 많은 FrontEnd 개발 프레임워크 및 javascipt 플러그인의 코딩 스타일도 하이픈 표기법을 사용하고 있으며, 프로젝트의 코드의 일관성을 유지하기 위해서도 하이픈 표기법 사용을 권장합니다.

> 주의 사항: 숫자, 대문자, 특수문자로 시작할 수 없습니다.

```javascript
<div class="slide-label n-3 back-swiper">
  <div class="swiper-wrapper">
    ...
  </div>
</div>
```

## 들여쓰기 {#html-1-4}

body 태그 안의 모든 요소는 중첩의 깊이에 따라 1탭 들여 씁니다. 1탭의 크기는 공백 2칸입니다.

```text
<body class="">
  <div class="ly-wrapper">
    <div class="ly-total-menu">
    ...
</div>
```

## 빈 줄 {#html-1-5}

그룹 되어있는 태그들을 구분하기 위하여 코드 간 1 줄의 빈 줄을 사용하는 경우가 있지만 이 경우 주석 사용을 권장하며 빈 줄을 사용하지 않습니다.

```text
/* bad */
<div class="section-login">

  <div class="login-before">
  ...
</div>
```

## 주석 {#html-1-6}

주석 기호와 내용 사이에는 반드시 공백이 한 칸 있어야 합니다. 시작 주석과 끝 주석 모두 작성하는 것을 권장합니다.

```markup
<!-- 2016.07.20 고객권리안내문 추가 -->
<ul class="policy">
  <li><a href="#none">이용약관</a></li>
  <li><a href="#none">개인정보처리방침</a></li>
  <li><a href="#none">고객권리안내문</a></li>
  <li><a href="#none">전자금융거래표준약관</a></li>
</ul>
<!--// 2016.07.20 객권리안내문 추가 -->
```

## 공백 {#html-1-7}

태그 명과 애트리뷰트, 애트리뷰트와 애트리뷰트 사이에 한 개의 공백이 필요하며 한 개 이상의 공백은 사용하지 않습니다.

> [Doctype](http://www.w3schools.com/tags/tag_doctype.asp)이 HTML5가 아닌 경우 종료 태그가 없는 태그의 닫는 규칙 앞에도 한 개의 공백이 필요합니다.

```javascript
<label for="checkboxA-1" class="label">체크 레이블</label>
<input type="checkbox" name="CA-1" id="checkboxA-1" class="checkbox">

// Doctypes XHTML일 경우 종료 태그 앞에도 한 개의 공백이 들어갑니다.
<img src="/img/logo.png" alt="logo" />
```

## 특수기호 {#html-1-8}

특수 기호는 문자 엔티티를 참조하여 작성합니다.

자주 사용하는 특수문자는 다음과 같습니다.

| Character | Entity Name |
| :--- | :--- |
| " | &quot; |
| & | &amp; |
| &lt; | &lt; |
| &gt; | &gt; |
| 공백 | &nbsp; |

* 엔티티 문자표: [http://www.w3schools.com/charsets/ref\_html\_entities\_4.asp](http://www.w3schools.com/charsets/ref_html_entities_4.asp)

## 종료태그 {#html-1-9}

Doctypes 선언에 따라 종료 태그가 없는 요소에 닫는 기호를 생략할 수 있습니다. HTML5를 사용한다면 닫는 기호를 생략해서 문서를 작성하고 XHTML을 사용한 경우는 닫는 기호를 반드시 사용합니다.

```text
// HTML
<input type="text>

// XHTML
<input type="text" />
```

종료 태그가 없는 요소는 다음과 같습니다.

> area,base, br, col, commend, embed, hr, img, input, keygen, link, meta, param, source

## DOCTYPE {#html-1-10}

보통 DTD라고 표현을 하며, HTML 문서를 작성할 때 가장 먼저 선언하게 됩니다. HTML5를 기본적으로 사용하며, 크로스 브라우징 범위에 IE9 이하 브라우저가 포함된다면 조건부 주석을 사용하여 'Shim' 처리합니다. 프로젝트의 정책상 HTML5를 사용하지 못하는 경우 HTML 4.01 Transitional, XHTML 1.0 Transitional 등을 사용할 수 있습니다.

> 도큐먼트 선언은 대소문자를 구분하지 않습니다.

```text
// HTML 5
<!DOCTYPE html>

// XHTML 1.0 Transitional
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

도큐먼트 타입 종류 : [http://www.w3schools.com/tags/tag\_doctype.asp](http://www.w3schools.com/tags/tag_doctype.asp)

**html5 및 반응형 shim 처리 방법**

```text
<!--[if lt IE 9]>
    <script src="../js/lib/html5shiv.js"></script>
    <script src="../js/lib/respond.min.js></script>
<![endif]-->
```

html5shiv.js 다운로드 : [https://github.com/aFarkas/html5shiv](https://github.com/aFarkas/html5shiv)

IE6 ~ IE8 반응형 구현 : [https://github.com/scottjehl/Respond](https://github.com/scottjehl/Respond)

## 기본언어 {#html-1-11}

lang 애트리뷰트는 User Agent가 언어를 올바르게 해석할 수 있게 도와주며, 검색과 음성 장치에 활용됩니다. en\(영어\), ja\(일본어\), zh-ch\(중국어\)입니다.

```text
// HTML
<html lang="en">
...
</html>

// XHTML
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
...
</html>
```

HTML 언어 코드 참조 : [http://www.w3schools.com/tags/ref\_language\_codes.asp](http://www.w3schools.com/tags/ref_language_codes.asp)

## HEAD 태그 구조 {#html-1-12}

&lt;head&gt;요소는 &lt;html&gt; 태그와 &lt;body&gt; 태그 사이에 위치합니다. 일반적으로 &lt;title&gt;, &lt;style&gt;, &lt;meta&gt;, &lt;link&gt;, &lt;script&gt;를 정의합니다.

**인코딩**

문서의 기본 인코딩은 uft-8로 설정합니다. 다른 인코딩 방식을 사용해야 할 경우 개발팀과 협의하에 결정합니다.

```text
<meta charset="utf-8">
```

**IE 랜더링 모드**

IE 브라우저에서 가장 최신 표준모드로 보이도록 설정합니다.

```text
<meta http-equiv="x-ua-compatible" content="ie=edge">
```

**제목**

본문 제목을 작성합니다.

```text
<title></title>
```

**뷰포트**

디바이스 상에서 최초 페이지를 로딩할 때 확대 정도, 최대 확대비율, 최소 확대비율 등을 다루는 속성입니다.

```text
<meta name="viewport" content="width=device-width, initial-scale=1">
```

뷰포트 더 알아보기 : [https://developer.mozilla.org/ko/docs/Mozilla/Mobile/Viewport\_meta\_tag](https://developer.mozilla.org/ko/docs/Mozilla/Mobile/Viewport_meta_tag)

**파비콘**

파비콘은 웹페이지에 접속했을 때, 상단 탭에 보이는 아이콘을 말합니다. 크로스 브라우징을 지원해야 한다면 웹 사이트의 루트 디렉터리에 16x16과 32x32의 favicon.ico 파일을 넣어 둡니다.

```text
<link rel="apple-touch-icon" href="apple-touch-icon.png">
```

파비콘 더 알아보기 : [http://webdir.tistory.com/337](http://webdir.tistory.com/337)

**스타일 선언**

CSS는 외부 파일에 작성해 사용합니다. 이러한 작업 방식을 External Type 방식이라 명칭합니다.

```css
/*  External Type  */
<link rel="stylesheet" href="css/normalize.css">
<link rel="stylesheet" href="css/main.css">
```

이메일 템플릿 작업이나 단발성으로 작성이 필요하다면 해당 파일의 &lt;head&gt; 요소에 &lt;style&gt; 태그를 사용해 작성합니다.

```css
/* Internal Type */
<style>
body {
  margin: 0;
  padding: 0;
}
</style>
```

문서의 스타일을 어떠한 조작이나 이벤트로 인하여 동적으로 변경해야 하는 경우에는 해당 요소의 style 애트리뷰트를 사용해 스타일을 직접 작성할 수 있습니다.

```css
/* Inline Type */
<div style="display: none">
...
</div>
```

**자바스크립트 선언**

웹 브라우저가 렌더링을 마치기 전에 자바스크립트로 어떠한 동작을 실행해야 한다면 &lt;head&gt; 요소 안에 스크립트를 선언합니다. 이런 상황이 아니라면 &lt;/body&gt; 태그 앞에 자바스크립트를 작성하는 것이 성능적인 측면에서 좋습니다.

```text
// 브라우저가 랜더링을 마치기 전에 실행할 파일을 선언한다.
<head>
  ...  
  <script src="js/vendor/modernizr-2.8.3.min.js"></script>
</head>
<body>
  ..
  // 모든 콘텐츠가 로드되고 실행될 스크립트 파일을 선언한다.
  <script src="js/main.js"></script>
</body>
```

**HTML 파일의 기본 구조**

```text
<!doctype html>
<html lang="ko">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <title></title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="apple-touch-icon" href="apple-touch-icon.png">
    <link rel="stylesheet" href="css/normalize.css">
    <link rel="stylesheet" href="css/main.css">
    <script src="js/vendor/modernizr-2.8.3.min.js"></script>
  </head>
  <body>

   ...
    <script src="https://code.jquery.com/jquery-{{JQUERY_VERSION}}.min.js"></script>
    <script>
    window.jQuery || document.write('<script src="js/vendor/jquery-{{JQUERY_VERSION}}.min.js"></script>')
    </script>

    <script src="js/plugins.js"></script>
    <script src="js/main.js"></script>
  </body>
</html>
```

