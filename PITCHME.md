## check-out

#### 今日やったこと

- Javascript中級者に向けて...！　
- jQueryに頼らない

---


### Javascript中級者に向けて...！

- スコープを理解する 
- [JavaScript本格入門](https://www.amazon.co.jp/%E6%94%B9%E8%A8%82%E6%96%B0%E7%89%88JavaScript%E6%9C%AC%E6%A0%BC%E5%85%A5%E9%96%80-%E3%83%A2%E3%83%80%E3%83%B3%E3%82%B9%E3%82%BF%E3%82%A4%E3%83%AB%E3%81%AB%E3%82%88%E3%82%8B%E5%9F%BA%E7%A4%8E%E3%81%8B%E3%82%89%E7%8F%BE%E5%A0%B4%E3%81%A7%E3%81%AE%E5%BF%9C%E7%94%A8%E3%81%BE%E3%81%A7-%E5%B1%B1%E7%94%B0-%E7%A5%A5%E5%AF%9B/dp/477418411X)(ch4)
- [javascript the good parts](https://www.amazon.co.jp/JavaScript-Parts-%E2%80%95%E3%80%8C%E8%89%AF%E3%81%84%E3%83%91%E3%83%BC%E3%83%84%E3%80%8D%E3%81%AB%E3%82%88%E3%82%8B%E3%83%99%E3%82%B9%E3%83%88%E3%83%97%E3%83%A9%E3%82%AF%E3%83%86%E3%82%A3%E3%82%B9-Douglas-Crockford/dp/4873113911)ほんの少し
---

### 変数はどの場所から参照できるか

#### グローバルスコープとローカルスコープ

- グローバルスコープとローカルスコープの2つがある
  - グローバルスコープ→スクリプト全体から参照できる
  - ローカルスコープ→定義された関数の中でのみ参照
  
---

### 変数はどの場所から参照できるか

#### グローバル変数とローカル変数の違い

- グローバル変数→関数の外で宣言
- ローカル変数→関数の中で宣言した変数

```js
var scope = "Global" 　//グローバル変数

function getValue() {
  var scope = "local Variable";　//ローカル変数
  return scope;
}
```

---

### ローカル変数の有効範囲は？

```js

var scope = "Global" 　

function getValue() {
  console.log(scope) 
  var scope = "local Variable";
  return scope;
  
}
```
Q.console.logの値は？

---

### 答え

##### A.未定義

javascriptではローカル変数は「関数全体で有効」
`console.log(scope)`の時点ではローカル変数scopeが有効になっているが、ローカル変数が確保されているだけで、var命令は実行されていない。

つまり`未定義`

このような挙動が不具合の原因となるので避けるべき...！

---

### 仮引数のスコープ(基本型と参照型)

基本型
```js
var value = 10

function decrementValue(value) {
  value--;
  return value;
}

console.log(value); //10
decrementValue(100) //99
```

---

### 仮引数のスコープ(基本型と参照型)

参照型（配列、オブジェクト、関数）

```js
var value = [1,2,4,8,16]

function decrementValue(value) {
  value.pop(); //末尾の要素を削除
  return value;
}

console.log(value)　//　①
decrementValue(value) //　②
console.log(value); //　③
```

Q. それぞれの①、②、③の値は？

---

### 答え

##### a. ①：1,2,4,8,16　 ②：1,4,8　 ③：1,4,8

参照型とは、値そのものではなく、値を格納したメモリ上の場所（アドレス）だけを格納している型

参照型の値を受け渡しをする場合、渡される値もメモリ上のアドレス情報だけとなる。（参照渡し）

---

### jQueryに頼らない

##### id, classで取得

idで取得

```js
$('#main')
```

```js
document.getElementById('main')
```
タグで取得

```js
$('div')
```

```js
document.getElementsByTagName('div')
```

classで取得

```js
$('.main')
```
```js
document.getElementsByClassName('main')
```

---


### おわり
