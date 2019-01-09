# コーディングガイドライン

---

## インデックス

1. 本規約の目的と方針
2. 対象ブラウザ
3. レスポンシブデザインの方針
4. 開発情報の確認
6. HTML
7. CSS
8. Javascript


---

## 本規約の目的と方針

---
### 方針
1. 文書構造的に正しいマークアップを行う。
2. 運用・拡張していく上で破綻が起きづらい全体設計をする。
3. 担当者が変わっても編集・変更しやすい技術・ツールを選定する。
4. コンポーネント指向を意識し再利用可能なソースを開発する。
5. ユーザーの閲覧環境を考慮した作りにする。
6. SEOが考慮されたコーディングを行う。
7. 本書とは別にガイドラインがある場合は、その都度確認してすすめる。

---

### 目的
- 納品物（Webサイトデータ）に一定の品質を担保する

---

# 対象ブラウザ

---

### Windows
- Internet Explorer 11
- Firefox 最新版
- Google Chrome 最新版

### Mac
- Safari 最新版

### スマートフォン
- iOS11 Safari


---

# HTML

---

## 書式の基本ルール

---

### HTTPSプロトコル
可能な限り、埋め込みリソースにはHTTPSプロトコルを使用する。

```
<!-- 推奨 -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

<!-- 可：プロトコルを省略（状況により使用可） -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

<!-- 非推奨：HTTPプロトコルを使用 -->
<script src="http://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

```

---

### 改行コード・文字コード
- 改行コード　CR+LF(Windows標準の改行コード)
- 文字コード　UTF-8

---
### 機種依存文字

機種依存文字およびHTML特殊文字（「&」「<」「>」ど）は、できる限り文字実体（エンティティ）参照に変換して記述する。

---

### インデント
インデントはスペース4つとする。  
タブを使用したり、タブとスペースを混在させたりしない。

```
<ul>
    <li>Fantastic</li>
    <li>Great</li>
</ul>
```

---

### 大文字・小文字の使用
小文字のみを使用する。  
HTML要素名、属性、属性値（text/CDATAを除く）、CSSセレクタ、プロパティ、およびプロパティ値（文字列を除く）は小文字を使用。

```
<!-- 推奨 -->
<img src="google.png" alt="Google">

<!-- 非推奨 -->
<A HREF="/">Home</A>
```

---

## HTMLスタイルルール

---

### ドキュメントタイプ
HTML5を使用する。  
要件に応じて、別の形式（XHTML 1.1 Strict、HTML 4.01 Strict、HTML 4.01 Transitional、など）を採用。


---

### タイプ属性
スタイルシートとスクリプトのtype属性は省略します。CSSとJavaScriptには型属性を使用しない。  
HTML5はデフォルトで text/css と text/javascript を意味するため、type属性を指定する必要はない。

```
<!-- 推奨 -->
<link rel="stylesheet" href="//www.google.com/css/maia.css">

<!-- 非推奨 -->
<link rel="stylesheet" href="//www.google.com/css/maia.css" type="text/css">

<!-- 推奨 -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- 非推奨 -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js" type="text/javascript"></script>
```

---

## HTML書式ルール

---

### マークアップ全般
文書内容に適したマークアップを行う。
目的に応じた要素（タグ）を使用する。たとえば、見出しには見出し要素、段落にはp要素、アンカーにはa要素などを使用する。

```
<!-- 推奨 -->
<a href="recommendations/">All recommendations</a>

<!-- 非推奨 -->
<div onclick="goToRecommendations();">All recommendations</div>
```

---

### 一行一要素
すべての要素は新しい行に配置する。要素の子要素であればインデントする。  
ただし、ブラウザがインライン要素として扱うタグ（em,spanなど）については一行に入れても問題ない。

```
<!-- 推奨 -->
<ul>
  <li>Moe</li>
  <li>Larry</li>
  <li>Curly</li>
</ul>

<!-- 推奨 -->
<blockquote>
  <p><em>Space</em>, the final frontier.</p>
</blockquote>

<!-- 非推奨 -->
<ul><li>Moe</li><li>Larry</li><li>Curly</li></ul>
```

---

### 閉じタグ
閉じタグの省略は行わない。  
可読性の低下を防ぐため。

```
<!-- 推奨 -->
<div class="hoge">All recommendations</div>

<!-- 非推奨 -->
<div class="hoge">All recommendations
```

---

### HTMLクォーテーション（引用符）
属性値を引用するときは、ダブルクォーテーション（二重引用符）を使用する。  
属性値の前後にはシングルクォーテーション（ ' ）ではなく、ダブルクォーテーション（ " ）を推奨する。
```
<!-- 推奨 -->
<a class="maia-button maia-button-secondary">Sign in</a>

<!-- 非推奨 -->
<a class='maia-button maia-button-secondary'>Sign in</a>
 ```
---

### hx要素
`<h1>`は、ページ固有のタイトルにあたるテキスト、もしくはimg要素に対して使用する。  
また、ページの文章構造に合わせてh2～5までを適宜使用する。  
`<h1>`はHTML5であっても複数使用をしない。  

```
<!-- 推奨 -->
<h1 class="page-ttl">Sign in</h1>

<section>
    <h2 class="sec-ttl">hogehoge</h1>
</section>


<!-- 非推奨 -->
<h1 class="page-ttl">Sign in</h1>

<section>
    <h1 class="sec-ttl">hogehoge</h1>
</section>
 ```
---

### 画像要素
意味のある画像は、原則背景ではなくimg要素として配置する。  
alt属性にて画像の代替となるテキストを設定する。特に指定がない場合はコーダーの判断で画像の簡易説明を設定する。  
「width=～」「height=～」は記述しない。サイズ変更はスタイルシートで行う。

```
<!-- 推奨 -->
<img src="sample.jpg" alt="サンプル画像">

<!-- 非推奨 -->
<img src="sample.jpg" width="200" height="100" alt="">
 ```
---

### コメントの挿入
ソース内容が把握しやすいよう、ブロックの後に必ずコメントを入れる。  
ID名を入れる場合「＃」は付けない。SSIインクルードとの競合を防ぐため。

```
<!-- 推奨 -->
<div id="content-wrap">

</div>
<!-- /content-wrap -->

<!-- 非推奨 -->
<div id="content-wrap">

</div><!-- /content-wrap -->
 ```
---

## SEO

---

### canonicalタグの設置
検索エンジンにURLが正しく認識されるよう、`<head>`内上部にcanonicalタグを設置。  
PCSPでソースが異なる場合はalternateタグも合わせて記述する。

```
<!-- 推奨 -->
<head>

<link rel="canonical" href="http://www.example.com/">

</head>
```
---

### 絶対パスによる記述
「トップページ」へのリンクは、絶対パスで記述。

```
<!-- 推奨 -->
<a href="https://www.example.com">トップページ</a>

<!-- 非推奨 -->
<a href="/">トップページ</a>
```

---
### テキストによるマークアップ（対策キーワードの盛り込み）
検索エンジンはテキストからページコンテンツを理解するため、文字の画像化を極力避け、  
Webフォント・スタイルシートなどを使用し、デザインの再現に努める。  
ただし、状況により画像テキストを使用する場合はalt属性の設置を必須とする。

---

### 構造化データ
構造化データはJSON-LDで記述する。  
データ内容は多岐に渡るため、要件に合わせ適切にマークアップすること。  
パンくずリストについては後述。

また、構造化データは必ず下記ツールにて実装テストを行うこと。  
[構造化データテストツール](https://search.google.com/structured-data/testing-tool/)  

---

### パンくずリストについて
新規に作成するWebサイトのパンくずリストは  
HTMLのマークアップ以外にJSON-LDでのマークアップを作成し、`<head>`内に記述する。  
その際必ず下記ツールにて実装テストを行うこと。  
[構造化データテストツール](https://search.google.com/structured-data/testing-tool/)  


```
<!-- パンくずリスト構造化データ作成例 -->
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "item": {
        "@id": "https://site-name.jp/",
        "name": "TOP"
      }
    }, {
      "@type": "ListItem",
      "position": 2,
      "item": {
        "@id": "https://site-name.jp/2/",
        "name": "第2階層"
      }
    }
  ]
}
</script>
```

---

### 画像圧縮について
画像圧縮はサイト表示速度改善に影響が大きいため  
デザインからスライスした画像を下記ツールを使用し、圧縮する。  
[compressor.io](https://compressor.io/)  

---
