# Arrow Function

本来 JavaScript で関数宣言時に使うのは`function`だが、
ES6 の導入から Arrow 関数が登場した。

```javascript
// 既存
const foo = function () {
  console.log("blah");
};

// Arrow
const foo = () => {
  console.log("blah");
};
```

Arrow 関数は`function`を使った関数と同じく動作するが、以下のような制約が存在する。

- 必ず匿名関数として使わなければならない。
- メソッドやコンストラクタとして使えない。

## :rabbit: JavaScript 関数の this バインディング

this にバインディングされる値は以下のようだ。

- 全域空間の this: 全域オブジェクト。
- メソッド呼び出し時のメソッド内部の this: 当メソッドを呼び出したオブジェクト。
- 関数呼び出し時の関数内部の this: **指定されない。**

例えば、

```javascript
const singer = {
  name: "Michael",
  foo1: function () {
    const foo2 = function () {
      console.log(this.name);
    };
    foo2();
  },
};

singer.foo1(); // undefined
```

`foo2`内部の this は指定されないため、全域オブジェクトを指すことになり、`undefined`になる。<br>

しかし、Arrow 関数を使えば、

```javascript
const singer = {
  name: "Michael",
  foo1: function () {
    const foo2 = () => {
      console.log(this.name);
    };
    foo2();
  },
};

singer.foo1(); // Michael
```

## :rabbit: Arrow 関数の this バインディング

**Arrow 関数には this が存在しない** <br>

> Arrow 関数には this という変数が存在しないため、その上位空間での this を参照することになる。

つまり、動的に this がバインディングされる`function`を使った関数宣言と異なり、宣言される時点での上位スコープが this にバインディングされる。

## :rabbit: Arrow 関数を使ってはいけない時

### メソッド

```javascript
const singer = {
    name: 'Michael',
    callName: () => console.log(this.name);
}

singer.callName(); // undefined
```

これは、`singer`オブジェクトではなく、上位スコープを指すことになってしまう。`function`を使うこと。

### コンストラクタ

```javascript
const Foo = () => {};
const foo = new Foo();
```

コンストラクタとしては使えない。

### addEventListener()の Callback 関数

```javascript
const h1 = document.querySelector("h1");

h1.addEventListener("click", function () {
  console.log(this); // h1 element
});

h1.addEventListener("click", () => {
  console.log(this); // window
});
```

> **この文書を作成したすべての原因** :innocent: <br>

`addEventListener`の Callback 関数には this に当イベントリスナーが呼び出された Element がバインディングされるように定義されている。このように、this の値が定まっている Callback 関数の場合、Arrow 関数を使うと既存の値が消え、上位スコープがバインディングされてしまう。
