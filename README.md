# コーディングガイドライン



## インデックス

1. 本規約の目的と方針
2. 対象ブラウザ
3. レスポンシブデザインの方針
4. ディレクトリ構成
6. HTML
7. CSS
8. Javascript




## 本規約の目的と方針


### 方針
1. 文書構造的に正しいマークアップを行う。
2. 運用・拡張していく上で破綻が起きづらい全体設計をする。
3. 担当者が変わっても編集・変更しやすい技術・ツールを選定する。
4. コンポーネント指向を意識し再利用可能なソースを開発する。
5. ユーザーの閲覧環境を考慮した作りにする。
6. SEOが考慮されたコーディングを行う。
7. 本書とは別にガイドラインがある場合は、その都度確認してすすめる。



### 目的
- 納品物（Webサイトデータ）に一定の品質を担保する



# 対象ブラウザ



### Windows
- Internet Explorer 11
- Firefox 最新版
- Google Chrome 最新版

### Mac
- Safari 最新版

### スマートフォン
- iOS11 Safari



# ディレクトリ構成



### 基本的なディレクトリ構成
- 新規かつスタティックな中規模サイト構築時の例
```
root/
├index.html
├assets/
│├css/
││ └ style.css
││
│├img/
││ ├ index/
││ │　 └.jpg
││ └ category01/
││ 　 　└.jpg
│└js/
│　├jquery.js
│　└common.js
│
│
└category01/
　└index.html
```
- シングルページ構築時の例
```
root/
├index.html
└assets/
　├css/
　│ └ style.css
　│
　├img/
　│ ├ index/
　│ │　 └.jpg
　│ └ category01/
　│ 　 　└.jpg
　└js/
　　├jquery.js
　　├page.js
　　└viewport.js
```



# HTML



## 書式の基本ルール



### HTTPSプロトコル
可能な限り、埋め込みリソースにはHTTPSプロトコルを使用します。

```
<!-- 推奨 -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

<!-- 可：プロトコルを省略（状況により使用可） -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

<!-- 非推奨：HTTPプロトコルを使用 -->
<script src="http://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

```



### 改行コード・文字コード
改行コード・文字コードは下記に設定します。

- 改行コード　CR+LF(Windows標準の改行コード)
- 文字コード　UTF-8


### 機種依存文字

機種依存文字およびHTML特殊文字（「&」「<」「>」など）は、できる限り文字実体（エンティティ）参照に変換して記述します。



### インデント
インデントは可読性を考慮しスペース4つとします。  
タブを使用したり、タブとスペースを混在させたりしないでください。

```
<ul>
    <li>Fantastic</li>
    <li>Great</li>
</ul>
```



### 大文字・小文字の使用  
HTML要素名、属性、属性値（text/CDATAを除く）、CSSセレクタ、プロパティ、およびプロパティ値（文字列を除く）は小文字のみを使用します。

```
<!-- 推奨 -->
<a href="/about/">About</A>

<!-- 非推奨 -->
<A HREF="/about/">Home</A>
```



## HTMLスタイルルール



### ドキュメントタイプ
新規作成のものは原則、HTML5を使用します。  
要件に応じて、別の形式（XHTML 1.1 Strict、HTML 4.01 Strict、HTML 4.01 Transitional、など）を採用する場合もあります。




### タイプ属性
スタイルシートとスクリプトのtype属性は省略します。  
HTML5はデフォルトで text/css と text/javascript を意味するため、type属性を指定する必要はありません。

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



## HTML書式ルール



### マークアップ全般
文書構造に適したマークアップを行います。
また、目的に応じた要素（タグ）を使用します。たとえば、見出しには見出し要素、段落にはp要素、アンカーにはa要素などを使用します。

```
<!-- 推奨 -->
<a href="recommendations/">All recommendations</a>

<!-- 非推奨 -->
<div onclick="goToRecommendations();">All recommendations</div>
```



### 一行一要素
すべての要素は新しい行に配置します。要素の子要素であればインデントしてください。  
ただし、ブラウザがインライン要素として扱うタグ（em,spanなど）については一行に入れても問題ありません。

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



### 閉じタグ
閉じタグの省略は、可読性の低下を防ぐために行いません。  


```
<!-- 推奨 -->
<div class="hoge">All recommendations</div>

<!-- 非推奨 -->
<div class="hoge">All recommendations
```



### HTMLクォーテーション（引用符）
属性値を引用するときは、シングルクォーテーション（ ' ）ではなく、  
ダブルクォーテーション（ " ）を推奨します。
```
<!-- 推奨 -->
<a class="maia-button maia-button-secondary">Sign in</a>

<!-- 非推奨 -->
<a class='maia-button maia-button-secondary'>Sign in</a>
 ```


### hx要素
`<h1>`は、ページ固有のタイトルにあたるテキスト、もしくはimg要素に対して使用します。  
また、ページの文章構造に合わせてh2～5までを適宜使用してください。  
`<h1>`はHTML5であっても複数使用をしません。  

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


### 画像要素
意味のある画像は、原則背景ではなくimg要素として配置します。  
alt属性にて画像の代替となるテキストを設定します。  
altの内容について特に指定がない場合はコーダーの判断で画像の簡易説明を設定します。  
「width=～」「height=～」は記述しません。サイズ変更はスタイルシートで行います。

```
<!-- 推奨 -->
<img src="sample.jpg" alt="サンプル画像">

<!-- 非推奨 -->
<img src="sample.jpg" width="200" height="100" alt="">
 ```


### コメントの挿入
ソース内容が把握しやすいよう、ブロックの後に必ずコメントを記述します。  
SSIインクルードとの競合などを防ぐため、セレクタは省略してください。

```
<!-- 推奨 -->
<div id="content-wrap">

</div>
<!-- /content-wrap -->

<!-- 非推奨 -->
<div id="content-wrap">

</div><!-- /#content-wrap -->
 ```


## SEO



### canonicalタグの設置
検索エンジンにURLが正しく認識されるよう、`<head>`内上部にcanonicalタグを設置します。  
PCSPでソースが異なる場合はalternateタグも合わせて記述します。

```
<!-- 推奨 -->
<head>

<link rel="canonical" href="http://www.example.com/">

</head>
```


### 絶対パスによる記述
「トップページ」へのリンクは、特に指定がない場合は絶対パスで記述します。

```
<!-- 推奨 -->
<a href="https://www.example.com">トップページ</a>

<!-- 非推奨 -->
<a href="/">トップページ</a>
```


### テキストによるマークアップ（対策キーワードの盛り込み）
検索エンジンはテキストからページコンテンツを理解するため、文字の画像化を極力避け、  
Webフォント・スタイルシートなどを使用し、デザインの再現に努めます。  
ただし、状況により画像テキストを使用する場合は、必ずalt属性を設置します。



### 構造化データ
構造化データはJSON-LDで記述します。  
データ内容は多岐に渡るため、要件に合わせ適切にマークアップしてください。  
パンくずリストについては後述。

また、構造化データは必ず下記ツールにて実装テストを行ってください。  
[構造化データテストツール](https://search.google.com/structured-data/testing-tool/)  



### パンくずリストについて
新規に作成するWebサイトのパンくずリストは  
HTMLのマークアップ以外にJSON-LDでのマークアップを作成し、`<head>`内に記述します。  
その際必ず下記ツールにて実装テストを行ってください。  
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



### 画像圧縮について
画像圧縮はサイト表示速度改善に影響が大きいため  
デザインからスライスした画像を下記ツールを使用し、圧縮する。  
[compressor.io](https://compressor.io/)



# CSS



### 文字コード
HTMLに合わせて記述します。原則UTF-8を使用。



### ID・Class名
原則、意味のある名前を設定します。

#### Class
Class名には`-`で要素名を繋ぐケバブケースを使用します。

```
<!-- 推奨 -->
<p class="body-copy">ダミーテキスト</p>

<!-- 非推奨 -->
<p class="body_copy">ダミーテキスト</p>
<p class="bodyCopy">ダミーテキスト</p>
```



### ID・Classの使い分け
IDはスタイル指定には使用しません。
アンカーリンクの対象となる要素を除き、原則としてClassのみを使用してコーディングしてください。  
アンカーリンクの対象となる要素に関しても、通常通りにClassでスタイルを付与した後に、アンカーリンク用としてIDを付与して下さい。



### CSS・SCSSについて
CSSの書き方に関するガイドラインは作業用ファイルに対して適応します。
Sassを標準で使用するになったため、コンパイル後のCSSについては



### セレクタの書き方
コンポーネント化したコーディングを前提としているためセレクタによる継承は極力行わないでください。  
継承は3つ程度までとします。  
また、要素セレクタは必要性がない場合は使用しないでください。

セレクタの複数並列記述については改行し、視認性・可読性を保つようにしてください。

```
<!-- 推奨 -->
.body-copy {
    font-size: 1.2rem;
}

<!-- 非推奨 -->
p.body-copy {
    font-size: 1.2rem;
}

.wrapper .contents .inner .body-copy {
    font-size: 1.2rem;
}
```
```
<!-- 推奨 -->
.red,
.blue,
.green {
    font-size: 1.2rem;
}

<!-- 非推奨 -->
.red,.blue,.green {
    font-size: 1.2rem;
}
```



### ショートハンド
ショートハンドの使用は推奨します。  
ただし、指定する値が一つの場合などは使用しないでください。  
スタイル継承時に2重指定や意図しないスタイルの適用などを引き起こします。

```
<!-- 推奨 -->
.style {
    margin: 30px 10px 10px;
}

.style.style-overwrite {
    margin-top: 40px;
}

<!-- 非推奨 -->
.style {
    margin: 30px 10px 10px;
}

.style.style--overwrite {
    margin: 40px 10px 10px;
}
```


### 汎用クラス
`.mgb-0 { margin-bottom: 0; }`などの汎用クラスは1要素への複数使用を推奨しません。

```
<!-- 推奨 -->
<p class="body-copy mgb-20">ダミーテキスト</p>

<!-- 非推奨 -->
<p class="body-copy mgb-20 mgr-10 pdb-20">ダミーテキスト</p>
```



# Javascript

