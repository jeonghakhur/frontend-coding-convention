# 네이밍 규칙

코드를 좀 더 예측 가능하고 유지 보수하기 쉽게 만드는 또 다른 방법은 네이밍 규칙입니다. 이 규칙을 통하여 읽기 쉽고 일관적이며 예측 가능한 코드를 생산해 낼 수 있습니다. 네이밍 규칙은 폴더, 파일, id 속성 값, clsass 속성 값, java script 변수와 함수 또는 메서드 등의 이름을 일관된 방식으로 결정하는 것입니다. 


### 기본사항

이름에 여러 단어가 들어간다면 단어를 구분하는 규칙을 사용합니다. 단어를 구분하는 방법에 따라 '언더스코어 표기법', '하이픈 표기법', '대문자 낙타 표기법', '소문자 낙타 표기법'으로 표현하도록 하겠습니다. 

**단어를 구분하는 표기 방법**
* 언더 스코어 표기법 : my_var
* 하이픈 표기법 : class-name
* 대문자 카멜 표기법 : MyConstructor
* 소문자 카멜 표기법 : gitfirstName

**공통 규칙** 

* 네이밍 조합의 순서는 형태, 의미, 상태, 순서의 순으로 조합하여 사용합니다.
* 순서의 경우 구분자를 지정하지 않고 마지막으로 조합된 문자에 붙여서 사용합니다. 동일한 이름이 존재하여 순서 조합을 사용할 경우 시작 숫자는 1부터 시작합니다.
* 네이밍의 길이를 줄이기 위하여 단축하여 사용하는 것을 허용합니다. 


```json
// 형태 + 의미 + 상태 + 순서
.box-alert-active-1

// 약어를 사용한 경우
CS(customer services)

// 단축하여 사용한 경우
src(soures) 

```

### 아이디

아이디는 _**소문자 카멜 표기법**_ 을 사용합니다. 스타일 지정을 위해 사용하지 않으며, DOM 조작을 위해 사용해야 합니다.

> 주의사항: 숫자, 대문자, 특수문자로 시작할 수 없습니다.


```javascript
<div id="boxToggle-1">토글박스</div>
<div id="boxToggle-2">토글박스</div>
```

### 클래스
아이디와 시각적 구분을 위해 _**하이픈 표기법**_을 사용합니다. 이미 수 많은 FrontEnd 개발 프레임워크 및 javascipt 플러그인의 코딩 스타일도 하이픈 표기법을 사용하고 있으며, 프로젝트의 코드의 일관성을 유지하기 위해서도 하이픈 표기법 사용을 권장합니다.

> 주의사항: 숫자, 대문자, 특수문자로 시작할 수 없습니다.

```css
* css *
.ly-wrapper {
  position: relative;
  overflow-x: hidden;
}
.ly-header {
  position: fixed;
  top: 0;
  z-index: 100;
  width: 100%;
  height: 45px;
  background-color: #428de7;
}
```
```javascript
<!-- HTML -->
<div class="slide-label n-3 back-swiper">
  <div class="swiper-wrapper">
  ...
  </div>
</div>
```

### 함수

일반 함수는 원시형 데이터 변수와 시각적으로 구분할 수 있도록 _**소문자 낙타 표기법**_을 사용합니다.

> 주의사항: 숫자, 대문자, 특수문자로 시작할 수 없습니다.

```javascript
function myFunction(p1, p2) {
  return p1 * p2;
}

```

### 생성자

```javascript
function myFunction(p1, p2) {
 return p1 * p2;
}
```

### 변수

```javascript
function myFunction(p1, p2) {
 return p1 * p2;
}
```




