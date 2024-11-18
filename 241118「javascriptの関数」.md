### 関数宣言vs関数表現式

関数の作り方には大きく関数宣言と関数表現式に分かれる。

```
// 関数宣言
function 関数の名(媒介変数) {
  // 関数の内容
  return リターン値
}

// 関数表現式
const 関数の名 = function(媒介変数) {
  // 関数の内容
  return リターン値
};
```

二つの方法にどんな違いがあるか？
まず関数宣言は、宣言より先に呼び出されても宣言部が上に引き上げられるHOISTINGが発生する。
反面、変数に割り当てて使う関数表現式は変数の特性上、宣言の以前には接近することができない。

```
hello(); // "Hello!"

function hello() {
  console.log("Hello!");
}
```

```
hello(); // ReferenceError: Cannot access 'hello' before initialization

const hello = function() {
  console.log("Hello!");
};
```

他にも表現式は匿名の関数で作ることができるし、主にcallback関数や変数に割り当てるとき使う。
関数宣言は一般的に独立的な関数に使う。

### 値として使われる関数

javascriptの関数は変数や他のデータ構造の中に割り当てられるし、違う関数のパラメータで伝達されたり、他の関数のリターンにもなれる。

```
// 変数に割当
const hello = function(){
	console.log('hello!');
};

hello(); // 'hello!'

// 客体のメソッドに割当
const obj = {
	name:'john',
	age:30,
	sayHi:function(){
		console.log('hello!');
	}
};

obj.sayHi(); // 'hello!'

// 配列に割当
 const arr = [
   1,
   "data",
   function () {
     console.log("hello!");
  },
];

arr[2](); // 'hello!'

// 他の関数にパラメータで伝達（CALLBACK関数）
function sayHi(){
	return 'Hi!';
};

function hello(greeting){
	console.log(greeting())
};

hello(sayHi); // 'Hi!'

// 他の関数のリターンになる(高次関数)
function getPrintHi(){
	return function (){
		console.log('Hi!');
	};
};

const sayHi = getPrintHi();

sayHi(); // 'Hi!'
getPringHi()(); // 'Hi!'
```

### 関数のパラメータとアーギュメント

関数の外から中に値を与える時、パラメータを活用できる。

```
function printThis(text) {
  console.log(text); 
} 
  
printThis("hi"); // 'hi'
printThis("hello"); // 'hello'

// 宣言部のtextがパラメータ,呼出部hi, helloがアーギュメント
```

パラメータのある関数にどんなアーギュメントも伝達しないとundefinedがでる。
この場合は基本値の設定はできる。

```
function greeting(name){
	console.log(`Hi! My name is ${name}!`);
}

greeting(); // 'Hi! My name is undefined!';
```

```
function greeting(name = 'John'){
	console.log(`Hi! My name is ${name}!`);
}

greeting(); // 'Hi! My name is John!';
```

可変的なアーギュメントで呼び出す関数の場合、レストーパラメータを使える。

```
function greet(greeting = "Hello", ...names) {
  console.log(`${greeting}, ${names.join(" and ")}`);
}

greet("Hi", "Alice", "Bob", "Charlie"); // Hi, Alice and Bob and Charlie
greet(); // Hello,
```

パラメータの基本値設定、レストーパラメータ機能は全部ES6（２０１５）以降の環境で使うことができる。

### やじるし関数

javascriptのES6から簡潔な文法で関数が定義できる。

```
// 一般的な関数表現式
const sayHi = function () {
	return console.log('hi');
}

// 矢印の形でfunctionキーワードの省略可能
const sayHi = () => {
	return console.log('hi');
}

// 動作部にreturn以外に他の動作が無いとreturnキーワードと中括弧の省略可能
const sayHi = () => console.log('hi');
```

他にもパラメータが一個の時、小かっこの省略のできるが可読性のため勧奨されない。

### javascriptのthis

javascriptでthisは、どう呼び出されたかによって参照する客体が違う。

1. 全域スコープでthisは、全域客体（ブラウザではWindow客体）を参照する。

```
console.log(this); // ブラウザ: window客体を出力
```

2. 一般関数では全域客体を参照（strict modeではundefined)

```
function showThis() {
  console.log(this);
}

showThis(); // ブラウザ: window, strict mode: undefined
```

3. 客体のメソッドでthisは該当の客体を参照

```
const obj = {
  name: "Alice",
  greet() {
    console.log(this.name);
  }
};

obj.greet(); // "Alice" (thisはobjを参照する。)
```

矢印の関数でのthisは一番近いコンテキストでthisをもってくるから、thisを活用する関数の宣言には矢印関数ではなく、一般的な関数の宣言が勧奨される。
他にも生成者関数として活用された場合の動作もあるが、これは次にクラスと生成者を扱う時間に述べる。
