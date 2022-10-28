# コンストラクター関数

```js
// 普通の関数とコンストラクター関数を明示的に分けるために
// コンストラクター関数は頭大文字にする
function Person(name, age) {
  this.name = name;
  this.age = age;
}
const bob = new Person('Bob', 18);
```

<br />

# prototype

オブジェクトに存在する特別なプロパティ
コンストラクタ関数と合わせて使用

```js
Person.prototype.hello = function () {
  console.log('hello' + this.name);
};
```

**なぜプロトタイプを使用するのか**  
→ **メモリの効率化のため。**  
\_\_proto\_\_ に同じ関数の参照が渡るため  
インスタンス化した際には prototype の参照が**proto**にコピーされる

<br />

# 関数コンストラクター

※一般的には使わない　関数は宣言して使う。

```js
const fn1 = new Function('a', 'b', 'return a + b');
const result = fn1(1, 2);
```

関数コンストラクターから関数を生成できる

<br />

# プロトタイプチェーン

自身のオブジェクト → prototype → Object の prototype

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.hello = function () {
    // 最初はこれ 1
  };
}
Person.prototype.hello = function () {
  // 次はこれ 2
};
Object.prototype.hello = function () {
  // さらに次 3
};
const bob = new Person('Bob', 18);
bob.hello();
```

<br />

# プロトタイプ継承

別のコンストラクター関数のプロトタイプを受け継いで、機能を流用できるようにすること。

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype.hello = function () {
  console.log('hello' + this.name);
};
function Japanese(name, age) {
  Person.call(this, name, age);
}
Japanese.prototype = Object.create(Person.prototype);
```

<br />

# クラス

コンストラクター関数をクラス表記で書けるようにしたもの。→ シンタックスシュガー

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  hello() {
    console.log('hello' + this.name);
  }
}
```

<br />

# クラス継承

```js
class Person {
  constructor(name, age) {
    this.name;
    this.age;
  }
  hello() {
    console.log('hello' + this.name);
  }
}
class Japanese extends Person {
  constructor(name, age, gender) {
    super(name, age);
    this.gender = gender;
  }
}
```

<br />

# setter, getter と static

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  // getter, setter
  get name() {
    return this.name;
  }
  set name(value) {
    this.name = val;
  }

  // static
  static hello() {
    console.log('static');
  }
}
Person.hello();
```

<br />

# private, public

```js
class Person {

    // private フィールド
    #privateField = 1;
    // public フィールド
    publicField = 2;

    // static な private フィールド
    static #staticPrivateField = 3;
    // static な public フィールド
    static staticPublicField = 4;

    // コンストラクタ
    constructor(name, age) {
        // フィールドを初期化できる (フィールドになくても → その場合はpublic？)
        #privateField = 1;
        publicField = 2;
        hogehogeField = 3;
    }

    // private getter
    get #computed() {
        return this.#privateField;
    }
    // public getter
    get computed() {
        return this.publicField;
    }

    // private setter
    set #computed(value) {
        this.#privateField = value;
    }
    // public setter
    set computed(value) {
        this.publicField = value;
    }

    // private メソッド
    #privateMethod() {

    }
    // public メソッド
    publicMethod() {

    }

    // static な private メソッド
    static #staticPrivateMethod() {

    }
    // static な public メソッド
    static staticPublicMethod() {

    }
}
```

<br />

# チェーンメソッド

一つのインスタンスに対して連続でメソッドを呼ぶ。

```js
return this;
```
