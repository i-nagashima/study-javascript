# Promise

### 重要

非同期処理をより簡単に、可読性が上がるように書けるようにしたもの。

```js
new Promise(function (resolve, reject) {
  // ここは同期処理
  resolve('hello');
  reject('bye');
})
  .then(function (data) {
    // 非同期処理（resolveを待つ）
    console.log(data); // -> 'hello'
    return data;
    // thenのなかでrejectをする場合
    // throw new Error();
  })
  .then(function (data) {
    // このdataは1つめのthenのreturnのdata;
    console.log(data);
  })
  .catch(function (data) {
    // 非同期処理（rejectを待つ）
    console.log(data); // -> 'bye'
  })
  .finally(function () {
    // 非同期処理（then, またはcatchを待つ）
    console.log('終了処理');
  });
```

<br />

# Promise チェーン

Promise を使って非同期処理を順次実行すること。  
非同期の処理を繋げるためには then のコールバック関数の戻り値に  
Promise のインスタンスを返すことが重要。

```js
function sleep(val) {
  return new Promise(function (resolve) {
    setTimeout(function () {
      console.log(val++);
      resolve(val);
    }, 1000);
  });
}
sleep(0)
  .then(function (val) {
    return sleep(val);
  })
  .then(function (val) {
    return sleep(val);
  })
  .then(function (val) {
    return sleep(val);
  });
```

<br />

# Promise と並列処理

```js
function sleep(val) {
  return new Promise(function (resolve) {
    setTimeout(function () {
      console.log(val++);
      resolve(val);
    }, val * 500);
  });
}
// Promise.all = 全て終わるまで
Promise.all([sleep(2), sleep(3), sleep(4)])
  .then(function () {
    console.log('end');
  })
  .catch(function (e) {
    console.error(e);
  });
// Promise.race = どれか終わるまで
Promise.race([sleep(2), sleep(3), sleep(4)])
  .then(function () {
    console.log('end');
  })
  .catch(function (e) {
    console.error(e);
  });
// Promise.allSettled = 全て終わるまでだが成功／失敗の状態も返す
Promise.allSettled([sleep(2), sleep(3), sleep(4)]).then(function (data) {
  console.log(data);
  console.log('end');
}); // catchにはいかない
```

<br />

# Await と Async

Promise を更に直感的に記述できるようにしたもの。  
※Promise が返ってくる関数には Await が使える

Async  
Promise を返却する関数の宣言を行う。

Await  
Promise を返却する関数の非同期処理が完了するまで待つ。

```js
function sleep(val) {
    return new Promise(function(resolve) {
        setTimeout(function() {
            console.log(val++);
            resolve(val);
        }, 1000);
    });
}
async function init() {
    let val = await sleep(0);
    val = await sleep(val);
    val = await sleep(val);
    val = await sleep(val);

    // 終わったあとにthenが呼び出される

    // エラーもいける
    //throw new Error();
}
init().then(function(val) {
    console.log(val);
}).catch(e) {
    console.error(e);
};
```

<br />

# fetch

WebApi の fetch は Promise を返す。  
だから Promise を使って処理を書くことができる

```js
// fetchはPromiseを返すのだからawaitが使える
// awaitを使うってことはasyncが必要なので
async function fetchUsers() {
  const response = await fetch('https://hoge.com/');
  const json = await response.json(); // json()もPromise返すので
  for (const user of json) {
    console.log(user.xxx);
  }
}
fetchUsers();
```

<br />

# 例外処理とエラー

```js
try {
} catch (e) {
} finally {
}

// Errorを継承してカスタムエラーを作る
class NoDataError extends Error {
  constructor(message) {
    super(message);
    this.name = 'NoDataError'; // これしないと'Error'で表示されちゃう
  }
}
```
