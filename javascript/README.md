# Javascript 코드 작성규칙

## 함수 {#javascript-1-1}

* 한문자 이름은 피하십시오. 이름에서 의도를 읽을 수 있도록 하십시오.

```javascript
// bad
function q() {
  // ...stuff...
}

// good
function query() {
  // ..stuff..
}
```

* 소문자 낙타표기법\(camelCase\)을 사용하십시오.

```javascript
function thisIsMyFunction() {};
```

* Class와 생성자에는 PascalCase를 사용하십시오.

```javascript
function User(options) {
  this.name = options.name;
}

var good = new User({
  name: 'yup'
});
```

* private 메서드나 프로퍼티명에 접두어로 밑줄을 붙여 구별하기 쉽게 합니다.

```javascript
// bad
var persion = {
  getName: function() {
    return this._getFirst() + ' ' + this._getLast();
  },
  _getFirst: function() {
    //...
  },
  _getLast: function() {
    //...
  }
};
```

## 변수\(Variable\) {#javascript-1-2}

* 변수는 밑줄로 단어를 분리하여 사용하십시오. 이렇게 하면 함수와 함수가 아닌 나머지 식별자\(즉 원시 데이터 타입과 객체\)를 시각적으로 구별하는 데 도움이 됩니다.

```javascript
var first_name, favorite_bands, old_company_name;
```

* 상수 및 전역 변수는 모든 글자를 대문자로 사용하십시오.

```javascript
var PI = 3.14,
    MAX_WIDTH = 960;
```

* 변수를 선언 할 때는 항상 var를 사용합니다. 그렇지 않으면 전역 변수로 선언됩니다.

```javascript
// bad
superPower = new SuperPower();

// good
var superPower = new SuperPower();
```

* 여러 변수를 선언하려면 하나의 var를 사용하여 변수마다 줄바꿈하여 선언합니다.

```javascript
// bad
var items = getItems();
var goSportsTeam = true;
var dragonball = 'z';

// good
var items = getItems(),
    goSportsTeam = true,
    dragonball = 'z';
```

* 정의되지 않은 변수를 마지막으로 선언합니다. 이것은 나중에 이미 할당된 변수 중 하나를 지정해야하는 경우에 유용합니다.

```javascript
// bad
var i, len, dragonball,
    items = getItems(),
    goSportsTeam = true;

// bad
var i, items = getItems(),
    dragonball,
    goSportsTeam = true,
    len;

// good
var items = getItems(),
    goSportsTeam = true,
    dragonball,
    length,
    i;
```

* 변수의 할당은 스코프의 시작 부분에서 해주십시오.

```javascript
// bad
function() {
  test();
  console.log('doing stuff..');

  //..other stuff..

  var name = getName();

  if (name === 'test') {
    return false;
  }

  return name;
}

// good
function() {
  var name = getName();

  test();
  console.log('doing stuff..');

  //..other stuff..

  if (name === 'test') {
    return false;
  }

  return name;
}

// bad
function() {
  var name = getName();

  if (!arguments.length) {
    return false;
  }

  return true;
}

// good
function() {
  if (!arguments.length) {
    return false;
  }

  var name = getName();

  return true;
}
```

## 오브젝트\(Objects\) {#javascript-1-3}

* Object를 만들 때는 리터럴 구문을 사용합니다.

  \`\`\`js

  // bad

  var item = new Object\(\);

// good var item = {};

```text
* 소문자 낙타표기법(camelCase)을 사용하십시오.

```js
// bad
var OBJEcttsssss = {};
var this_is_my_object = {};
var this-is-my-object = {};
// good
var thisIsMyObject = {};
```

## 배열\(Arrays\) {#javascript-1-4}

* 배열을 만들 때 리터럴 구문을 사용합니다.

```javascript
// bad
var items = new Array();

// good
var items = [];
```

## 문자열\(Strings\) {#javascript-1-5}

* 문자열은 작은 따옴표 `''`를 사용합니다.

```javascript
// bad
var name = "Bob Parr";

// good
var name = 'Bob Parr';

// bad
var fullName = "Bob " + this.lastName;

// good
var fullName = 'Bob ' + this.lastName;
```

* 80 문자 이상의 문자열은 문자열 연결을 사용하여 여러 줄에 걸쳐 기술 합니다.

```javascript
// bad
var errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// good
var errorMessage = 'This is a super long error that ' +
  'was thrown because of Batman.' +
  'When you stop to think about ' +
  'how Batman had anything to do ' +
  'with this, you would get nowhere ' +
  'fast.';
```

* 프로그래에서 문자열을 생성할 필요가 있는 경우 문자열 연결 대신 Array\#join을 사용합니다.

```javascript
var items,
    messages,
    length,
    i;

messages = [{
    state: 'success',
    message: 'This one worked.'
},{
    state: 'success',
    message: 'This one worked as well.'
},{
    state: 'error',
    message: 'This one did not work.'
}];

length = messages.length;

// bad
function inbox(messages) {
  items = '<ul>';

  for (i = 0; i < length; i++) {
    items += '<li>' + messages[i].message + '</li>';
  }

  return items + '</ul>';
}

// good
function inbox(messages) {
  items = [];

  for (i = 0; i < length; i++) {
    items[i] = messages[i].message;
  }

  return '<ul><li>' + items.join('</li><li>') + '</li></ul>';
}
```

## 속성\(Propertie\) {#javascript-1-6}

* 속성에 액세스하려면 도트.를 사용합니다.

```javascript
var luke = {
  jedi: true,
  age: 28
};

function getProp(prop) {
  return luke[prop];
}

var isJedi = getProp('jedi');
```

* 변수를 사용하여 속성에 접근하려면 대괄호\[\]을 사용하십시오.

```javascript
var luke = {
  jedi: true,
  age: 28
};

function getProp(prop) {
  return luke[prop];
}

var isJedi = getProp('jedi');
```

## 암묵적 타입캐스팅 피하기 {#javascript-1-7}

* == 나 != 보다는 === 와 !== 를 사용합니다.

```javascript
var zero = 0;

// bad
if (zero == false) {
  // 이 블록은 실행된다.
}
// good
if (zero === false) {
  // zero는 0이고 false가 아니기 때문에 이 블록은 실행되지 않는다.
}
```

## 블록\(Blocks\) {#javascript-1-8}

* 수행 블록은 중괄호 \({}\)를 사용합니다.

```javascript
// bad
if (test)
  return false;

// good
if (test) return false;

// good
if (test) {
  return false;
}

// bad
function() { return false; }

// good
function() {
  return false;
}
```

## 주석\(Comments\) {#javascript-1-9}

* 복수행의 코멘트는 `/** ... */` 를 사용해 주십시오. 그 안에는 설명과 모든 매개 변수와 반환 값에 대한 형식과 값을 설명합니다.

```javascript
// bad
// make() returns a new element
// based on the passed in tag name
//
// @param <String> tag
// @return <Element> element
function make(tag) {

  // ...stuff...

  return element;
}

// good
/**
 * make() returns a new element
 * based on the passed in tag name
 *
 * @param <String> tag
 * @return <Element> element
 */
function make(tag) {

  // ...stuff...

  return element;
}
```

* 한 줄 주석에는`//`를 사용하십시오. 코멘트를 추가하고 싶은 코드의 상단에 작성하십시오. 또한 주석 앞에 빈 줄을 넣어주십시오.

```javascript
// bad
var active = true;  // is current tab

// good
// is current tab
var active = true;

// bad
function getType() {
  console.log('fetching type...');
  // set the default type to 'no type'
  var type = this._type || 'no type';

  return type;
}

// good
function getType() {
  console.log('fetching type...');

  // set the default type to 'no type'
  var type = this._type || 'no type';

  return type;
}
```

> 문제를 지적하고 재고를 촉구하거나 문제에 대한 해결책을 제시하는 등 의견의 앞에 `FIXME` 나 `TODO`를 붙이는 것으로 다른 개발자의 빠른 이해를 도울 수 있습니다. 이러한 어떤 액션을 동반한다는 의미에서 일반 코멘트와는 다릅니다. 액션은 `FIXME - 해결책이 필요` 또는 `TODO - 구현이 필요` 입니다.

* 문제에 대한 코멘트로 `// FIXME :`를 사용하십시오.

```javascript
function Calculator() {

  // FIXME: 전역 변수를 사용해서는 안됩니다.
  total = 0;

  return this;
}
```

* 문제 해결책에 대한 코멘트로 `// TODO :`를 사용하십시오.

```javascript
function Calculator() {

  // TODO: total은 옵션 매개 변수로 설정되어야 함.
  this.total = 0;
  return this;
}
```

## 공백\(Whitespace\) 및 들여쓰기\(indentation\) {#javascript-1-10}

* 탭에는 공백 2개를 설정하십시오.

```javascript
// bad
function() {
∙∙∙∙var name;
}

// bad
function() {
∙var name;
}

// good
function() {
∙∙var name;
}
```

* if-else, 객체 리터럴의 여는 중괄호\({\)전, 닫는 중괄호\(}\)와 else 또는 while 사이에 공백하나를 입력합니다.

```javascript
// if-else
if (a) {
  ...
} else {
  ...
}

// good
dog.set('attr', {
  age: '1 year',
  breed: 'Bernese Mountain Dog'
});
```

* for 루프의 여는 대괄호전, 쉼표, 피연산자와 구성요소를 분리하는 세미콜론 다음 공백을 하나 입력합니다.

```javascript
for (var i = 0, max = 10; i < max; i += 1) {...}
```

* 배열의 원소들은 분리하는 쉼표다음 공백을 하나 입력합니다.

```javascript
var a = [1, 2, 3];
```

* 객체의 프로퍼티를 분리하는 쉼표 다음, 프로퍼티의 이름과 값을 분리하는 콜론 다음 공백을 하나 입력합니다.

```javascript
var o = {a: 1, b: 2};
```

* 함수의 인자들을 분리할 때 공백을 하나 입력합니다.

```javascript
myFunc(a, b, c);
```

* 함수를 정의하는 중괄호 전에 공백을 하나 입력합니다.

```javascript
function myFunc() {...};
```

* 익명 함수 표현식에서 function 다음에 공백을 하나 입력합니다.

```javascript
var myFunc = function() {...};
```

* 모든 연산자와 피연산자 사이에 공백을 하나 입력합니다. 즉 `+, - < *, =, <, >, <==, >==, ===, !==, &&, ||, +=` 등의 앞뒤에 공백을 하나 입력합니다.

```javascript
//bad
var d= 0,
    a = b+1;
if (a&& b&&c) {
  d=a $c;
  a+=d;
}
//good
var d = 0,
    a = b + 1;
if (a && b && c) {
  d = a % c;
  a += d;
}
```

* 메소드 체인이 길어지는 경우 적절히 들여쓰기\(indentation\) 합니다.

```javascript
// bad
$('#items').find('.selected').highlight().end().find('.open').updateCount();

// good
$('#items')
  .find('.selected')
    .highlight()
    .end()
  .find('.open')
    .updateCount();

// bad
var leds = stage.selectAll('.led').data(data).enter().append('svg:svg').class('led', true)
    .attr('width',  (radius + margin) * 2).append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);

// good
var leds = stage.selectAll('.led')
    .data(data)
  .enter().append('svg:svg')
    .class('led', true)
    .attr('width',  (radius + margin) * 2)
  .append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);
```

## 빈줄 {#javascript-1-11}

* 파일의 마지막에는 하나의 빈줄을 넣어주세요.

```javascript
// bad
(function(global) {
  // ...stuff...
})(this);
```

```javascript
// good
(function(global) {
  // ...stuff...
})(this);
```

## jQuery {#javascript-1-12}

* jQuery Object의 변수 앞에는 $을 부여해 주십시오.

```javascript
// bad
var sidebar = $('.sidebar');

// good
var $sidebar = $('.sidebar');
```

* jQuery 쿼리결과를 캐시해주십시오.

```javascript
// bad
function setSidebar() {
  $('.sidebar').hide();

  // ...stuff...

  $('.sidebar').css({
    'background-color': 'pink'
  });
}

// good
function setSidebar() {
  var $sidebar = $('.sidebar');
  $sidebar.hide();

  // ...stuff...

  $sidebar.css({
    'background-color': 'pink'
  });
}
```

