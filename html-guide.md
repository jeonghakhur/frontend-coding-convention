## HTML 코드 작성 규칙

### 기본 사항
* DTD를 제외한 모든 요소와 애트리뷰트는 소문자로 작성합니다.
* 애트리뷰트 값은 큰 따옴표("")로 묶습니다.
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
 HTML5가 아닌 경우 종료 태그가 없는 태그의 닫는 규칙 앞에도 한 개의 공백이 필요합니다. 

```javascript
// Doctypes HTML5일 경우
<input type="text>

// Doctypes XHTML일 경우
<input type="text" />
```

### 특수기호

특수 기호는 문자 엔티티를 참조하여 작성합니다.

자주 사용하는 특수무자는 다음과 같습니다.

| Character | Entity Name |
|---
| " |
| & |
| < |
| > |
| space |
 &amp;quot; | &amp;amp; | &amp;lt; | &amp;gt; | &amp;nbsp; |



* [엔티티 문자표](http://www.w3schools.com/charsets/ref_html_entities_4.asp): http://www.w3schools.com/charsets/ref_html_entities_4.asp
