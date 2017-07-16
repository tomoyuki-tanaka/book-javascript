# 変数

## ３種類の宣言

2015年にECMAScriptS2015\(ES6\)が正式勧告されてとても話題になりました。今回は今後標準になっていくであろう記述方法と、まだまだレガシーな環境で開発しなければならない方の為に古いES5までの記述方法と合わせて紹介していきます。

## variable文

変数の代入は以下のように行います。型情報を明示する必要はありません。というより素のJavaScriptでは型アノテーションなどは今のところ存在しません。型によるチェックが欲しい場合は`Flow.js`や`TypeScript`を使用することで実現でます。

```js
var foo = 'foo';
foo = 1; // 再代入可能・異なる型を代入可能
var foo = [1, 2]; // 同じスコープで再宣言可能
```

## let文

ES2015以降はletを使って変数宣言ができます。IE11も対応しているのでプロジェクトの対象ブラウザによっては使用可能ですが、レガシーなJavaScripが既にある場合は混在させない方が良いでしょう。`var`との違いは同じスコープで同じ名前の変数を再度宣言することができないことと、後述するスコープの範囲が異なるという２点があります。

```js
let bar = 'bar';
bar = 1
let bar; // SyntaxError: Identifier 'bar' has already been declared
```

## const文

こちらも`let`同様にES2015で策定された新しい構文です。IE11の対応についても同様です。`let` と異なる点は再代入ができないことです。`constant`つまり定数です。大文字を使う必要はありませんし、再代入はできるだけしない方が良いので**ほとんどの場合、変数宣言にconstを使用します。**

```js
const buz = 'buz';
buz = 1 // TypeError: Assignment to constant variable.
```

他の言語の定数でも同様ですが`const`はあくまで再代入を防ぐものであって値を変更できなくするわけではありません。ですので変数の中身がオブジェクトなどの参照値の場合は破壊的変更を行うメソッドなどで変更することができます。

```js
const obj = { foo: 'foo' }
obj.foo = 'hoge' // objのプロパティは変更できる
obj.foo // 'hoge'

const arr = []
arr.push(1) // 末尾に引数 1 を追加する
arr[0] // 1
```

### もう一つの宣言方法

実はもう一つ、変数を宣言する方法があります。と言っても基本的には使ってはいけない方法です。それは`var`などの文を頭におかずに変数を宣言する方法です。この場合は実際には変数ではなくグローバルオブジェクトと呼ばれるものにプロパティを追加することになります。スコープが全体に広がるので危険ですし、グローバルオブジェクトがもともと持つプロパティを上書きしてしまう恐れがありますから基本的には使ってはいけません。（jQueryなどのライブラリはこの方法で`$`や`jQuery`というプロパティにアクセス可能にしています）

```js
bar = 'bar' // barを一度も宣言してない状態で代入すると・・
window.bar //=>'bar' windowオブジェクトにbarプロパティを追加してしまった！
```


