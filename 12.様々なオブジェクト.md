# Proxy

プロパティの操作に独自の処理を追加するためのオブジェクト。

```js
const targetObj = { a: 0 }
const handler = {
    // target = ターゲットのオブジェクト
    // prop = プロパティ
    // value = プロパティの値
    // receiver = Proxyのオブジェクト
    set: function(target, prop, value, receiver) {
        console.log(`[set]: ${prop}`);
        // setの中で値をセットしないければいけない
        target[prop] = value;
    }
    get: function(target, prop, receiver) {
        console.log(`[get]: ${prop}`);
        return target[prop];
    }
    deleteProperty: function(target, prop) {
        console.log(`[delete]: ${prop}`);
        // deletePropertyの中で値を削除しないければいけない
        delete target[prop];
    }
}
const pxy = new Proxy(targetObj, handler);
pxy.a = 1;
pxy.a;
delete pxy.a;
```

<br />

# Reflect

JS エンジンの内部の汎用的な関数を呼び出すメソッドが格納されているオブジェクト。  
なぜあるか／どういうふうに使うか

1. 内部メソッドを呼び出す関数の格納場所 // うーん使わないかな
2. Proxy と合わせて使用するため。

<br />

# WeakMap

弱い参照でオブジェクトを保持するコレクション  
※キーは必ずオブジェクト  
※正直使い所がよくわからん

<br />

# JSON

JSON.parse  
 JSON → Object

JSON.stringify  
 Object → JSON

```js
const obj = { a: 0, b: 1, c: 2 };
const json = JSON.stringify(obj);
const obj2 = JSON.parse(json);
```

<br />

# Storage

ブラウザの保存領域にデータを格納するためのオブジェクト

```js
localStrage.setItem('key', 'value');
const result = localStrage.getItem('key');
```
