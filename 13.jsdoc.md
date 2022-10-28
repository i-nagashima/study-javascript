# 最低限の JSDoc

最低限の JSDoc はこれ

# 基本

```ts
/** ほげほげ */

/**
 * ほげほげ
 */
```

# 変数

```ts
/** @type {string} ほげの変数 */
const hoge = 'hoge';
```

# 関数 (プリミティブ)

```ts
/**
 * 引数でもらった値をそのまま返します。
 * @param {string} value 値
 * @return {string} そのままの値
 * @throws {Error}
 */
const hoge = (value: string): string => {
  return value;
};
```

# 関数 (オブジェクト)

```ts
/**
 * 引数でもらった値をそのまま返します。
 * @param {{ v: number }} value 値
 * @return {{ v: stirng }} そのままの値
 * @throws {Error}
 */
const hoge = (value: { v: stirng }): { v: stirng } => {
  return value;
};
```

# 関数 (オブジェクト簡易版)

```ts
/**
 * 引数でもらった値をそのまま返します。
 * @param {Object} value 値
 * @return {Object} そのままの値
 * @throws {Error}
 */
const hoge = (value: { v: stirng }): { v: stirng } => {
  return value;
};
```

# クラス

```ts
/**
 * クラスの説明
 * @extends {B}
 */
class C extends B {
  /** プロパティ */
  private value: string;
  /**
   * コンストラクタ
   * @param {string} data データ
   */
  constructor(data: string) {}
  /**
   * メソッドっす
   * @param {string} value 値
   * @return {string} そのままの値
   * @throws {Error}
   */
  fn(value: string): string {
    return value;
  }
}
```
