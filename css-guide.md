## CSS 코드 작성 규칙

### 기본 규칙

* 모든 속성은 숫자, 대문자, 특수문자로 시작할 수 없으며, 영문 소문자로 작성합니다.

* 단어의 구분을 위하여 하이픈 표기법을 사용합니다.

* 마지막 속성 값의 끝에도 세미콜론을 사용합니다.

* 방향에 따라 속성을 지정해야 하는 경위 top, right, bottom, left 순으로 작성합니다.


### 선택자 구분

스타일 엔진은 다음 4개의 카테고리로 스타일 규칙을 분류합니다.

1. ID 규칙

2. Class 규칙

3. Tag 규칙

4. Universal 규칙


이 4개의 규칙들은 스타일 규칙을 적용하는데 기본적인 역할을 하므로 이해하는 것이 중요합니다.

**키 선택자**

선택자의 마지막 선택자를 의미합니다**. **아래 코드에서 키 선택자는 img, p, \[title\]이 됩니다. 따라 마지막 작성된 키 선택를 기준으로 규칙을 분류할 수 있습니다.

```
a img, div > p, h1 + [title] {...}
```

**ID 규칙**

```
button#backButton {…} /* 이건 ID 규칙이다. */
#urlBar[type="autocomplete"] {…} /* 이것도 ID 규칙이다. */
treeitem > treerow > treecell#myCell:active {…} /* 이것도 ID 규칙이다. */
```

**Class 규칙**

```
button.toolbarButton {…} /* Class 규칙 */
.fancyText {…}    /* Class 규칙 */
menuitem > .menu-left[checked="true"] {…} /* Class 규칙 */
```

**Tag 규칙**

```
td {…} /* Tag 규칙 */
treeitem > treerow {…} /* Tag 규칙 */
input[type="checkbox"] {…} /* Tag 규칙 */
```

**Universal 규칙**

```
[hidden="true"] {…} /* universal 규칙 */  
* {…}        /* universal 규칙 */
tree > [collapsed="true"] {…} /* universal 규칙 */
```

### 선택자 작성 규칙

스타일 엔진은 키 선택자로 부터 시작하여 왼쪽으로 이동하면서 엘리먼트가 규칙에 적합한지를 확인하게 됩니다. 만약 엘리먼트가 이 규칙에 적합하거나 적합하지 않다는게 확인되면 멈추게 됩니다.

가장 기본적인 개념은 규칙 필터링입니다. 위에서 소개한 4개의 규칙 카테고리는 관계없는 규칙을 제거하기 위함입니다. 따라서 스타일 엔진은 엘리먼트와 관계없는 규칙을 매칭하는데 시간을 낭비하지 않을 수 있습니다.

성능을 비약적으로 향상시키는 방법은 바로 매칭을 줄이는 것입니다. 주어진 엘리먼트가 적합한지 확인하는데 고려해야할 규칙의 수가 적을수록 성능이 좋아지게 됩니다.

**효일적인 CSS를 작성하기 위한 방법**

* 선택자는 상위 선택자를 포함하여 3개 이상 작성되지 않게 합니다.

* 전체 선택자를 사용하지 않습니다.

* 정규표현식과 유사한 애트리뷰트 선택자 사용을 지양하며, 부적합한 애트리뷰트 선택자 사용을 지양합니다.

* 아이디 선택자를 사용하지 않습니다.

* 클래스 규칙에 불필요한 태그를 조합하여  사용하지 않습니다.

* 태그 선택자 규칙에 상위 선택자로 태그를 포함하지 않습니다.


**선택자 개수 제한**

선택자를 작성할 때 키 선택자\(가장 오른쪽에 위치하며, 마지막에 작성된 선택자를 지칭합니다.\)를 포함하여, 상위 선택자는 3개 이상 작성되지 않는 것을 권장합니다.

```css
.select-1, .select-2, .select-3 {...}
section div span {...}
```

**전체 선택자의 사용.**

전체 선택자는 `*` 같은 형태로 작성되며 한 번에 모든 요소에 대응됩니다. 브라우저는 선택자를 오른쪽에서 왼쪽으로 읽기 때문에 마지막에 전체 선택자를 사용한 경우 최초 문서내의 모든 요소에 대응하고 그 이후 상위 클래스로 해당 요소를 선택하는지 확인하는 과정을 거치게 됩니다. 따라서 요소를 선택하는 CSS 규칙이 깊어지는 경우와 전체 선택자를 마지막 부분에 작성하는 경우 브라우저의 성능 저하가 발생하기 때문에 사용을 지양해야 합니다.

```
/* bad */
* {...}
.selector * {...}

/* better */
.selector * th {...}
```

**애트리뷰트 선택자의 사용**

키 선택자로 애트리뷰트 선택자를 사용한 경우는 최초 문서 내의 모든 태그에 해당 애트리뷰와 속성 값이 있는지를 확인하여, 브라우저의 성능저하가 발생하게 되므로 사용하지 않습니다.

```
/* bad */
[type="text"] {...}
.label [type="checkbox"] {...}

/* better */
input[type="text"] {...}
.layer-pop[data-role="popup"] .header {...}
```

CSS3는 정규표현식 처럼 속성 값에 따라 대응되는 선택자가 추가 되었습니다. 그러나 성능적인 측면으로 살펴보면, 클래스를 기반으로 하는 방식 보다 속도가 떨어지게 되므로 사용하지 않습니다.

```
/* bad */
/* 지정한 문자열이 속성값에 포함하는 요소에 대응 */
.regex-selector[type*="value"] {...}

/* 지정한 문자열이 속성 값으로 시작하는 요소에 대응 */
.regex-selector[type^="value"] {...}

/* 지정한 문자열이 속성값으로 끝나는 요소에 대응 */
.regex-selector[type$="value"] {...}

/* 지정한 문자열이 공백으로 나누어진 속성값을 포함하는 요소에 대응 */
.regex-selector[type~="value"] {...}

/* 지정한 문자열이 '-'로 나누어진 속성값을 포함하는 요소에 대응 */
.regex-selector[type|="value"] {...}
```

다음 두 경우는 성능에 영향을 미치지 않는다.

```
/* better */
/* 지정한 문자열이 속성값에 일치하는 요소에 대응 */
.regex-selector[type="value"] {...}

/* 지정한 속성명에 일치하는 요소에 대응 */
.regex-selector[type] {...}
```

**아이디 선택자의 사용.**

ID는 하나의 HTML 파일에 유일하게 존재해야하는 값입니다. ID 선택자를 사용한 다는 것은 그 스타일을 한 요소에만 사용하게 된다는 것을 의미하게 됩니다. 이러한 구조는 스타일 규칙의 재 사용이 불가능하게 만들어 CSS 파일 사이즈를 크게 만들고, 유지보수와 확장성에 불편함을 가져오게 됩니다.

```
/* bad */
#container {...}
```

> 레이아웃 요소에도 ID 규칙을 사용하지 않습니다.

**태그와 클래스 선택자의 사용.**

태그와 클래스 조합으로 불필요하게 사용된 선택자는 사용하지 않아야 합니다. 고유한 이름의 클래스를 작성해 안전하게 사용할 수 있는 방법을 사용하며, 불필요한 태그를 조합하여 사용하지 않으므로 파일 용량을 줄이는 동시에 태그에 대응할 필요가 없기 때문에 브라우저의 성능도 높일 수 있습니다.

```
/* bad */
.guide-box li.selected::after {...}

/* better */
input.radio {...}
```

**태그와 태그 선택자의 사용.**

HTML 문서 수정에 따른 CSS 파일 수정을 최소화하기 위해서 태그 규칙에 상위 선택자로 태그 선택자를 사용하지 않습니다.

```
/* bad */
.notice-box li span {...}

/* better */
.notice-box .list .span {...}
```

### **@Charset**

스타일 시트에 쓰이는 문자 인코딩을 지정합니다. 스타일 시트의 첫 번째 요소로 작성되어야 하며 어떤 문자도 @Charset 앞에 작성되지 말아야 합니다. 요소가 작성되지 않으며 utf-8로 가정합니다.

```
@charset "utf-8"
```

> 파일을 저장할 때는 반드시 선언한 문자셋과 동일한 인코딩으로 저장해야 합니다. 에디터 프로그램의 종류와 IDE 종류에 따라 인코딩 방식을 변경하는 것이 다르기 때문에 이 문서에서 인코딩 저장 방법을 별도로 설명하지 않습니다.

### @import

개발 진행시 편의를 위하여 @import를 사용하여 분기되어 있는 다른 파일의 스타일 규칙을 import 할 수 있습니다. 하지만 성능의 문제로 인하여 배포전 CSS 파일을 통합하여 사용하거나 link 태크를 사용하여 병렬로 import 할 수 있게 처리합니다.

```
@import url(common.css);
@import url(main-2.css);
```

줄바꿈

### 들여쓰기

코드의 가독성과 유지보수를 위하여 중첩의 깊이에 따라 공백 2칸을 들여쓰기 합니다. 운영 서비스에 반영할 경우 minify하여 파일 용량을 줄여 배포하도록 합니다.

```
html {
  position: relative;
  margin: 0 auto;
  ...
}

@media (width:320px) {
  .input-text.jumin {
    width: 46.1%;
  }
}
```

### 공백

중괄호의 시작 앞, 속성의 콜론 뒤, 속성 값 사이에 하나의 공백을 작성합니다.

```
/* 중괄 시작 앞 */
input {...}

/* 속성의 콜론 뒤 */
.input-text {
  box-sizing: border-box;
}

/* 속성 값 사이 */
.box-error {
  border: 1px soild #eeeeee;
}
```

### 속성 우선순위

아래의 나와 있는 순서로 작성하는 것을 권장합니다. csscomb 와 같은 빌드 스크립트를 이용하여 서비스 반영 전에 우선순위 및 코드를 정리할 수 도 있습니다.

1. display

2. list-style

3. position

4. float

5. clear

6. width \/ height

7. padding \/ margin

8. border \/ background

9. color \/ font

10. text-decoration

11. text-align \/ vertical-align

12. white-space

13. other text

14. content


cssComb.js :[ https:\/\/github.com\/csscomb\/csscomb.js](https://github.com/csscomb/csscomb.js)
cssComb 속성 우선 순위 설정 보기 : [https:\/\/github.com\/csscomb\/csscomb.js\/tree\/dev\/config](https://github.com/csscomb/csscomb.js/tree/dev/config)

### 세미콜론

마지막 속성의 값 뒤에도 세미 콜론을 작성합니다. 속성과 속성 사이에 세미콜론이 빠져 발생하는 오류를 사전에 방지하고, 속성의 추가 삭제 및 위치 변경에도 효율적이기 때문입니다.

```
.btn-type-2.checked {
  color: #fff;
  background-color: #428de7;
  border: none;
  border: 1px solid #428de7;
}
```

### 빈줄

CSS 파일에는 빈줄을 사용하지 않으며 빈줄이 들어간 경우 서비스 반영 전, 빈줄을 제거하고 배포합도록 합니다.

```
/* bad */
body {
  ...
}

.ly-wrapper {
  ...
}
```

### 주석

주석 기호와 내용 사이에는 반드시 공백이 한 칸 있어야 합니다. 시작 주석만 작성하며 끝 줗석은 작성하지 않습니다.

```
/* layout */
html {
  ...
}
```

### 큰 따옴표

다음과 같은 경우 큰 따옴표를 사용하며, 그 밖의 속성에는 사용하지 않습니다.

* @charset 속성의 값

```
@charset "uft-8";
```

### 작은 따옴표

다음과 같은 경우 작은 따옴표를 사용하며, 그 밖의 속성에는 사용하지 않습니다.

* font-family 속성의 폰트명에 공백이 포함된 경우와 한글명의 폰트를 사용한 경우

* @font-face 속성의 url 값 및 format 값

* background 속성의 url 이미지 경로

* content 속성의 값


```
font-family: 'ns-r';

src: url('../font/NotoSans/NotoSans-Light.eot?#iefix') format('embedded-opentype');

background: url('../img/bg-btn-collapse.png') no-repeat;

content: '';


```

### 예약어

