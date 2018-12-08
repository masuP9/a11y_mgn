# アクセシブルなウェブの実装のためにWAI-ARIAを使いこなす

## わたしについて

## 今日のお話

1. はじめに
2. WAI-ARIAとは
3. WAI-ARIAの前にHTML
4. WAI-ARIAを使いこなす
5. 実際のワークフロー

## はじめに

### フロントエンドの実装が担保するウェブアクセシビリティ

### 実装腕力

息を吐くようにアクセシブルな実装をする

## WAI-ARIAとは

## WAI-ARIAの前にHTML

### 適切な要素選択

####  `<a href>` / `<button>`

- 遷移と実行
- フォーカス可能ということ

1. [リンクかボタンかそれ以外か \- Unreviewed](http://takenspc.hatenablog.com/entry/2013/10/21/063807)

#### `<h1>` / `<section>`

- 画面の領域分割とラベリング

#### `<table>` / `<th>`

- データ構造を示す

#### `input`  / `label`

NG

```html
<dt>会社名</dt>
<dd><input type="text" /></dd>
```

OK

```html
<label>
  会社名 <input type="text" />
</label>
```

##### `<datalist>`

(e.g. [大阪のセレクトショップZABOUの通販/ウェブショップ](https://shop.zabou.org/)

### HTMLの属性

#### `alt` / `title`

```html
<a href="#" class="right-off-canvas-toggle show-for-small globalNavButton" aria-expanded="true">
  <img src="https://www.m-g-n.me/wp-content/themes/mgn/src/svg/sandwich.svg">
</a>
```

----

```html
<abbr title="point">pt</abbr>
```

#### `tabindex`

- 値は順序
- 1以上にせず、 `0` or `-1` を使用する

### Read the HTML Living Standard

[4 The elements of HTML](https://html.spec.whatwg.org/multipage/#toc-semantics)

## WAI-ARIAを使う時の考え方

WAI-ARIAはホスト言語のセマンティクスを補強する

- HTMLで表現できないものを表現する時
- どうしてもHTMLのネイティブ要素が使えない時
- 構造上、ネイティブのセマンティクスを上書きする必要がある時

### HTMLで表現できないものを表現する時

- HTMLにない`role`
- ステート、プロパティ

#### よく使う `role`

- `alert`
- `dialog`
- `tab`
- `search`

#### 頻出ステート、プロパティ

- `aria-expanded`
- `aria-hidden`
- `aria-controls`
- `aria-current`
- `aria-label`
- `aria-describedby`
- `aria-assertive`

### どうしてもHTMLのネイティブ要素が使えない時

- そんなときは無いハズ

### 構造上、ネイティブの`role`やプロパティを上書きする必要がある時

- `role="none"`
- `aria-hidden`

## WAI-ARIAを使う時に参照する資料やドキュメント

### オーサリングプラクティス

### ARIA in HTML

## WAI-ARIA の検証

### ブラウザの Accessibility Tree

### 実際にスクリーンリーダーで検証してみる

## 実際のコーディングの流れ