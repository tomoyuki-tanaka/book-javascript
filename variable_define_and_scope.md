# 変数とスコープ

Javaなどの型宣言を行うタイプの静的型付け言語のユーザーはしばしば「JavaScript（やRuby）には型が無い」と言う方がいます。これは誤りで動的型付け言語という名の通り、実行時に型が変化するためそのような誤解が生まれています。実際コーディングする際には型を意識して記述しなければ行けません。（当たり前ですが）

そして動的型付けだからといってそこまで構えることもありません。良い書き方をすれば変数の状態を気にして混乱することもありません。

## JavaScriptにおける型

変数について説明する前にJavaScriptの型について簡単に説明します。型には以下のものが存在します。

* プリミティブ型（Immutableつまり不変の値、変数には値そのものが入る\)
  * Boolean `true`
  * Null `null`
  * Undefined  `undefined`
  * Number `1`
  * String ```'foo' "bar" `buz`(``はES6以降のみ)```
  * Symbol （ES2015以降\)
* オブジェクト（変数には参照が入る）
  * オブジェクトリテラル `{ foo: "bar" }`
* * 配列　`[1, 2, 3]`
  * 関数 `function f() { ... }`
  * etc..

## ３種類の宣言

2015年にECMAScriptS2015\(ES6\)が正式勧告されてとても話題になりました。今回は今後標準になっていくであろう記述方法と、まだまだレガシーな環境で開発しなければならない方の為に古いES5までの記述方法と合わせて紹介していきます。

## variable文

```js
var foo = 'foo'; // JavaScriptではchar型はなく文字列は''でも""でも構いません
```


