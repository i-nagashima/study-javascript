# 関数

関数にオーバーロードはない。  
そのため関数式で関数は定義したほうがよい

```js
// エラーにならない
function fn(a, b) {}
function fn(a) {}

// エラーになる
const fn = function (a, b) {};
function fn(a) {}
```

<br />

# 関数とオブジェクト

### 重要

関数は実行可能なオブジェクトである

```js
// オブジェクトだからプロパティやメソッドを追加できる
function a() {}
a.prop = 0;
a.method = function () {};
```

<br />

# コールバック関数

他の関数に引数として渡される関数

```js
function a() {
  console.log('a call');
}
function b(a) {
  a();
}
b(a);
// 無名関数で
b(function () {
  console.log('no name call');
});
```

<br />

# 参照のコピーと'this'

オブジェクトのメソッド　として実行される場合  
'this' => 呼び出し元オブジェクト

関数 として実行される場合  
'this' => グローバルオブジェクト

<br />

# コールバック関数と'this'

参照のコピーと'this' と同じ

<br />

# bind と'this'

bind によって this（や引数）を固定した新しい関数を生成。

```js
function a() {
  console.log('hello ' + this.name);
}
const b = a.bind({ name: 'hoge' });
b();
```

<br />

# call, apply と'this'

bind  
'this'や引数の参照先を変更。使用時点で実行はしない。

call, apply  
'this'や引数の参照先を変更。同時に関数を実行する。

```js
function a() {
  console.log('hello ' + this.name);
}
const hoge = { name: 'hoge' };
a.apply(hoge); // この時点で実行する
a.call(hoge); // この時点で実行する
```

call は 第 2 引数に a の引数を指定できる。  
apply は 第 2 引数に配列を指定する。関数では配列が展開される。

<br />

# アロー関数

無名関数を記述しやすくした省略記法

```js
const b = (name) => {
  return name;
};
const b = (name) => name;
const b = (name, name2) => name + name2;
```

無名関数とアロー関数の違い

|           | 無名関数 | アロー関数 |
| :-------- | :------: | :--------: |
| this      |    ○     |     ☓      |
| arguments |    ○     |     ☓      |
| new       |    ○     |     ☓      |
| prototype |    ○     |     ☓      |

<br />

# アロー関数と'this'

アロー関数は'this'を取らないので

```js
const person = {
  name: 'hoge',
  hello: () => {
    console.log(this.name);
  },
};
person.hello(); // 表示されない or グローバル（window）のname
```
