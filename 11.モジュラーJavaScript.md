# ES Modules と CommonJS

CommonJS (CJS)  
Node.js  
require / exports  
.cjs

ES Modules (ESM)  
ECMAScript (Browser)  
import / export  
.mjs

<br />

# import と export

script では

```js
<script type='module' src='module.js'></script>
```

export

```js
export let publicVal = 0; // プリミティブをexportは普通しない
export function publicFn() {
  console.log('publicFn called');
}
export default 0;
```

import

```js
import { publicVal, publicFn } from './module.js';
import { publicVal as val, publicFn as fn } from './module.js';
// default
import defaultVal, { publicVal, publicFn } from './module.js';
// 全部
import defaultVal, * as module from './module.js';

// 単純にスクリプトを実行したい場合
import 'mmodule.js'; // from がいらない
```

<br />

# モジュールコンテキストとモジュールスコープ

モジュールコンテキスト  
this は使うことができない // グローバルでは使えない

<br />

# Strict モード

通常の JavaScript で許容されている一部の書き方を制限する。

- 意図しないバグの混入の防止
- 予約後の確保
- コードのセキュア化

'use strict'  
ファイルの先頭、もくは関数内の先頭行に記述

<br />

# Strict モードとクラス

クラスの中では Strict モードが on になっている。

<br />

# ダイナミックインポート

※対応していないブラウザがある  
Promise が返ってくる

```js
import('module.js').then(function (modules) {
  modules.xxx();
});
```

```js
// Async/Await
async function fn() {
  const modules = await import('./module.js');
  modules.xxx();
}
fn();
```
