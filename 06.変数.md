# 暗黙的な型変換

変数が呼ばれた状況によって変数の型が自動的に変換されること。  
typeof <変数> で型がわかる

<br />

# 厳格な等価性と抽象的な等価性

比較演算子  
厳格な等価性　　 a === b 型の比較あり  
抽象的な等価性　 a == b 型の比較なし

<br />

# プリミティブ型とオブジェクト

プリミティブ型  
string number boolean undefined null symbol bigint  
オブジェクト  
プリミティブ型以外

<br />

# 参照と分割代入

分割代入  
オブジェクトから特定のプロパティを抽出して宣言を行う。

```js
let { a, b } = object;
```

名前を変える場合

```js
let { a: a2, b: b2 } = object;
a2 = ;
b2 = ;
```

関数の引数で分割代入をする

```js
function fn({ prop }) {
    prop = ;
}
```
