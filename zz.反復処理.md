# ループ文

```js
for (let i = 0; i < 10; i++) {}
while (true) {}
```

<br />

# ループ文とブロックスコープ

```js
// 期待どおりの値 0 2 4 6 8
for (let i = 0; i < 5; i++) {
  const j = i * 2;
  setTimeout(function () {
    console.log(j);
  }, 1000);
}
// 期待されない値 8 8 8 8 8
for (let i = 0; i < 5; i++) {
  var j = i * 2;
  setTimeout(function () {
    console.log(j);
  }, 1000);
}
// → これはforの上でvarを宣言しているのと同じ
```

<br />

# for...in と列挙可能性

列挙可能プロパティに対して順不同で反復処理を実行する。

```js
const obj = {
    prop1: 'value1'.
    prop2: 'value2'.
    prop3: 'value3'.
}
Object.prototype.method = functiohn() {}
for(let key in obj) {
    console.log(key, obj[key]);
}
```

<br />

# for...of と反復可能性

イテレーターを持つオブジェクトの反復操作を行う。  
string array map set arguments etc...

```js
const arry = ['a', 'b,' 'c'];
for(let v of arry) {
    console.log(v);
}
```

<br />

# Map と Set

コレクションのこと

```js
const map = new Map();

const key = {};
map.set(key1, 'value1');
const v1 = map.get(key);

const key2 = function () {};
map.set(key2, 'value2');
const v2 = map.get(key2);

let key3 = 0;
map.set(key3, 'value3');
const v3 = map.get(key3);

map.delete(key3); // 削除

const s = new Set();
s.add(key1);
s.add(key2);
s.add(key3);
s.delete(key3); // 削除
```

<br />

# イテレーター

```js
function genIterator(max) {
  let i = 0;
  return {
    next: function () {
      if (i >= max) {
        return {
          done: true,
        };
      } else {
        return {
          done: false,
          value: i++,
        };
      }
    },
  };
}
```

<br />

# ジェネレーター

イテレーターを生成するための特殊な関数  
→ より簡略化して記述可能

```js
function* gen() {
  if (ループ継続) {
    yield 値; // done: false, value: 値
  } else {
    return 値; // done: true, value: 値
  }
}
```
