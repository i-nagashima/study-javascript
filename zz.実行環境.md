# 実行コンテキスト

コードを実行する際の文脈・状況

1. グローバルコンテキスト
2. 関数コンテキスト
3. eval コンテキスト　 → 　非推奨

<br />

# コールスタック

実行中のコードがたどってきたコンテキストの積み重ね

```js
function a() {}
function b() {
  a();
}
function c() {
  b();
}
c();

--- コールスタック
グローバル
c
b
a
```

<br />

# ホスティング

コンテキスト内で宣言した変数や関数の定義を  
コード実行前にメモリーに配置すること。（宣言の巻き上げ）

```js
// 大丈夫
a();
function a() {
    console.log();
}

// 大丈夫(undefined)
console.log(b); // undefined
var b = 0;

// エラー
console.log(c);
let c = 0;
const c = 0;

// 関数の中でも同じ
function() {
    a();
    function a() {
        console.log();
    }
}

// ただし、関数式の場合は変数と同じだからダメ。
```
