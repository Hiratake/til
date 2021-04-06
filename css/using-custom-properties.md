# カスタムプロパティの使用

CSSカスタムプロパティは、CSS内で使用できる変数のようなもの。[var()関数](https://developer.mozilla.org/ja/docs/Web/CSS/var())を使用することで他のプロパティの中で使用することができる。

## 基本的な使い方

2つのハイフンから始まるプロパティ名と、その後に何らかの値を記述することで、カスタムプロパティを宣言することができる。  
カスタムプロパティ名には「英数字」「アンダースコア」「ハイフン」を使用することができ、「大文字」「小文字」は区別される。

```css
element {
  --color-primary: #fff;
}
```

カスタムプロパティにはさまざまな値を格納することができる。

```css
element: {
  --color-primary: #fff;
  --color-secondary: 255, 255, 255;
  --font-size: 16px;
  --gradient-primary: linear-gradient(150deg, #fff, #000);
  --position-default: left center;
  --image-url: url('https://example.com/image.png');
}
```

宣言したカスタムプロパティを使用する場合は、 `var(プロパティ名)` と記述する。

```css
element {
  --color-primary: #fff;
  color: var(--color-primary);
}
```

## カスタムプロパティの継承

カスタムプロパティにはスコープがあり、宣言したセレクタ内でしか使用することはできない。

```html
<div class="A"></div>
<div class="B"></div>
```
```css
.A {
  --color-primary: #fff;
}
.B {
  /* 使用できない */
  color: var(--color-primary);
}
```

ただし、カスタムプロパティは継承されるため、親要素のカスタムプロパティを使用することは可能である。 `:root` 擬似クラス（HTMLでは `<html>` 要素を表す）で宣言することで、全体でカスタムプロパティを使用することができる。

```css
:root {
  --color-primary: #fff;
}
```

継承したカスタムプロパティの値を上書きすることもでき、上書きした値はそのセレクタ内でのみ有効となる。

```html
<div class="A">
  <div class="B"></div>
  <div class="C"></div>
</div>
```
```css
.A {
  --color-primary: #fff;
}
.B {
  --color-primary: #000;
  color: var(--color-primary); /* #000 となる */
}
.C {
  color: var(--color-primary); /* #fff となる */
}
```

## カスタムプロパティのフォールバック

`var()` 関数では、変数が宣言されていない場合に使用する代替値を用意しておくことができる。  
以下の場合、 `--primary-color` が宣言されていない場合は `#ececec` となる。

```css
element {
  color: var(--primary-color, #ececec);
}
```

`var()` 関数はネストすることができる。

```css
element {
  color: var(--primary-color, var(--secondary-color, #ececec));
}
```

## Classやdata属性で値を切り替える

`:root` 疑似クラスは、HTMLでは `<html>` 要素を表す。そのため、 `<body>` に付与した class や data 属性によってカスタムプロパティの値を変更したい場合は、以下のように記述すれば良い。

```html
<!DOCTYPE html>
<html lang="ja">
  <head>
    <meta charset="utf-8">
  </head>
  <body data-theme="dark">
    <!-- Contents -->
  </body>
</html>
```
```css
:root {
  --color-primary: #f5f5f5;
}
:root [data-theme="dark"] {
  --color-primary: #2c2c2c;
}
```

## ウィンドウ幅で値を切り替える

カスタムプロパティとメディアクエリを組み合わせることで、ウィンドウ幅に応じてカスタムプロパティの値を変更することができる。

```css
:root {
  --gap-base: 8px;
}
@media only screen and (min-width: 768px) {
  :root {
    --gap-base: 16px;
  }
}
```

## 無効となるケース

カスタムプロパティに `url()` 関数を格納することはできるが、 `url()` 関数内でカスタムプロパティに格納した画像URLを使用することはできない。

```css
:root {
  --image-url: 'https://example.com/image.png';
}
element {
  background-image: url(var(--image-url)); /* 無効な値 */
}
```

## 参考

- [CSS カスタムプロパティ (変数) の使用 - CSS: カスケーディングスタイルシート | MDN](https://developer.mozilla.org/ja/docs/Web/CSS/Using_CSS_custom_properties)
- [CSSの変数（カスタムプロパティ）便利な使い方を詳しく解説 | コリス](https://coliss.com/articles/build-websites/operation/css/css-variables.html)
- [CSSで変数（カスタムプロパティ）を使ってみよう | Webクリエイターボックス](https://www.webcreatorbox.com/tech/css-variables)