## HTML 코드 작성 규칙

### 기본 사항

* DTD를 제외한 모든 요소와 애트리뷰트는 소문자로 작성합니다.
* 애트리뷰트 값은 큰 따옴표\(""\)로 묶습니다.
* 아이디와 클래스의 속성 값은 숫자, 대문자, 특수문자로 시작할 수 없습니다.
* 애트리뷰트의 속성의 값은 숫자, 특수문자로 시작할 수 없으며, 대문자로는 시작할 수 있습니다.

### 아이디

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

#### 클래스

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

### 들여쓰기

body 태그 안의 모든 요소는 중첩의 깊이에 따라 1탭 들여 씁니다.

1탭의 크기는 공백 2칸입니다.

### 빈줄

그룹 되어있는 태그들을 구분하기 위하여 코드간 1 줄의 빈 줄을 사용하는 경우가 있지만 이 경우 주석 사용을 권장하며 빈줄을 사용하지 않습니다.

### 주석

주석 기호와 내용 사이에는 반드시 공백이 한 칸 있어야 합니다. 시작 주석과 끝 주석 모두 작성하는 것을 권장합니다.

```HTML
<!-- 2016.07.20 고객권리안내문 추가 -->
<ul class="policy">
  <li><a href="#none">이용약관</a></li>
  <li><a href="#none">개인정보처리방침</a></li>
  <li><a href="#none">고객권리안내문</a></li>
  <li><a href="#none">전자금융거래표준약관</a></li>
</ul>
<!--// 2016.07.20 객권리안내문 추가 -->
```

### 공백

태그명과 애트리뷰트, 애트리뷰트와 애트리뷰트 사이에 한 개의 공백이 필요하며 한개 이상의 공백은 사용하지 않습니다.

> [Doctypes](http://www.w3schools.com/tags/tag_doctype.asp)이
>  HTML5가 아닌 경우 종료 태그가 없는 태그의 닫는 규칙 앞에도 한 개의 공백이 필요합니다.

```javascript

<label for="checkboxA-1" class="label">체크 레이블</label>
<input type="checkbox" name="CA-1" id="checkboxA-1" class="checkbox">

// Doctypes XHTML일 경우 종료 태그 앞에도 한 개의 공백이 들어갑니다.
<img src="/img/logo.png" alt="logo" />
```

### 특수기호

특수 기호는 문자 엔티티를 참조하여 작성합니다.

자주 사용하는 특수무자는 다음과 같습니다.

| Character | Entity Name |
| --- | --- |
|  | Entity Name |
| " | " |
| & | & |
| &lt; | &lt; |
| &gt; | &gt; |

* [엔티티 문자표](http://www.w3schools.com/charsets/ref_html_entities_4.asp): [http:\/\/www.w3schools.com\/charsets\/ref\_html\_entities\_4.asp](http://www.w3schools.com/charsets/ref_html_entities_4.asp)

### 종료태그

Doctypes 선언에 따라 종료태그가 없는 요소에 닫는 기호를 생략할 수 있습니다. HTML5를 사용한다면 닫는 기호를 생략해서 문서를 작성하고 XHTML을 사용한 경우는 닫는 기호를 반드시 사용합니다.

```
// Doctypes HTML5일 경우
<input type="text>

// Doctypes XHTML일 경우
<input type="text" />
```

종료태그가 없는 요소는 다음과 같습니다.

> area,base, br, col, commend, embed, hr, img, input, keygen, link, meta, param, source

### DOCTYPE

보통 DTD라고 표현을 하며, HTML 문서를 작성할 때 가장 먼저 선언하게 됩니다. HTML5를 기본적으로 사용하며, 크로스브라우징 범위에 IE9 이하 브라우저가 포함된다면 조건부 주석을 사용하여 'Shim[^1]' 처리합니다. 프로젝트의 정책상 HTML5를 사용하지 못하는 경우 HTML 4.01 Transitional, XHTML 1.0 Transitional 등을 사용할 수 있습니다.

> 도큐먼트 선언은 대소문자를 구분하지 않습니다.



> Shim이란

도큐먼트 타입 종류 : [http:\/\/www.w3schools.com\/tags\/tag\_doctype.asp](http://www.w3schools.com/tags/tag_doctype.asp)

**html5 및 반응형 shim 처리 방법**

```
<!--[if lt IE 9]>
    <script src="../js/lib/html5shiv.js"></script>
    <script src="../js/lib/respond.min.js></script> 
<![endif]-->
```

html5shiv.js 다운로드 : [https:\/\/github.com\/aFarkas\/html5shiv](https://github.com/aFarkas/html5shiv)

IE6 ~ IE8 반응형 구현 : [https:\/\/github.com\/scottjehl\/Respond](https://github.com/scottjehl/Respond)

### 기본언어

lang 에크리뷰트는 User Agent가 언어를 올바르게 해석할 수 있게 도와주며, 검색과 음성장치에 활용됩니다.  en\(영어\), ja\(일본어\), zh-ch\(중국어\) 입니다.



브라우저 버전에 혹은 브라우저의 벤더에 따라 특정 기능을 지원하지 못하는 상황이 발생하게 되는데 이러한 것을 파편화라고 합니다. 개발자에게는 브라우저 파편화는 골치 아픈 문제 중 하나인데 파편화를 줄이기 위해, 비슷한 결과를 만들기 위한 방법을 'Shim'이라고 합니다.



