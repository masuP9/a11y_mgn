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
- `aria-live`

### どうしてもHTMLのネイティブ要素が使えない時

HTMLの持つ機能を代替的に実装する場合

```html
<input type="datatime-local" />
```

```html
<div aria-expanded="true">
    <input role="combobox" type="text" aria-haspopup="grid" aria-activedescendant="date-2018-12-09" />
    <div role="grid">
        table widget...
    </div>
</div>
```

----

通常のHTMLネイティブ要素を装飾のためだけに代替しなくても良い

```html
<span role="checkbox" aria-checked="true" tabindex="0"></span>
```

```html
<input type="checkbox" checked style="opacity: 0;/* visually hidden style */" />
<span aria-hidden="true">
    <svg>...</svg>
</span>
```

### 構造上、ネイティブの`role`やプロパティを上書きする必要がある時

例) `role[tablist] > role[tab]` 

```html
<ul role="tablist">
    <li role="tab"></li>
</ul>
```

```html
<ul role="tablist">
    <li role="none">
        <a href="#tabpanel-1" role="tab">Tab</a>
    </li>
</ul>
```

## WAI-ARIAを使う時に参照する資料やドキュメント

### [WAI\-ARIA Authoring Practices 1\.1](https://www.w3.org/TR/wai-aria-practices-1.1/)

### [ARIA in HTML](https://www.w3.org/TR/html-aria/)

[ARIA in HTML 日本語訳](https://momdo.github.io/html-aria/)

## WAI-ARIA の検証

### ブラウザの Accessibility Tree

Chrome: デベロッパーツール > Elements > Accessibility

Firefox: 開発ツール > アクセシビリティ

Safari: 開発ツール > 要素 > ノード > アクセシビリティ

Edge: 開発者ツール > 要素 > アクセシビリティのプロパティ

### 実際にスクリーンリーダーで検証してみる

- ナレーター
- NVDA
- VoiceOver

## 実際のコーディングの流れ