# グローバルスコープとスクリプトスコープ

Windows オブジェクト　  ＝　グローバルスコープ  
一般的にはスクリプトスコープもグローバルスコープと呼ばれる

<br />

# 関数スコープとブロックスコープ

ブロックスコープは　 if とかです。  
ブロックスコープの中で var を使用するとブロックスコープにはならない  
ブロックスコープの中で関数宣言をしてもブロックスコープにならない  
関数式は大丈夫 const d = function(){}

<br />

# レキシカルスコープ

コードを書く場所によって参照できる変数が変わるスコープのこと。

1. 実行中のコードから見た外部スコープのこと。
2. どのようにしてスコープを決定するかの仕様のこと。

<br />

# スコープチェーン

<br />

# クロージャー

レキシカルスコープの変数を関数が使用している状態

1. プライベート変数の定義ができる

```js
function incrementFactory() {
  let num = 0;
  function increment() {
    num = num + 1;
    console.log(num);
  }
  return increment;
}
const increment = incrementFactory();
increment();
increment();
```

2. 動的な関数の生成

```js
function addNumberFactory(num) {
  function addNumber(value) {
    return num + value;
  }
  return addNumber;
}
const add5 = addNumberFactory(5);
const add10 = addNumberFactory(10);
const result15 = add5(10); // 15
const result20 = add10(10); // 20
```

<br />

# 即時関数

関数定義と同時に一度だけ実行される関数。

```js
let result = (function (仮引数) {
  return 戻り値;
})(実引数);

(function () {
  console.log(hoge);
})();

(() => {
  console.log(hoge);
})();
```
