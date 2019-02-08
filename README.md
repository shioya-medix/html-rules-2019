# コーディングガイドライン



## インデックス

1. 本規約の目的と方針
2. 対象ブラウザ
3. ディレクトリ構成
4. HTML
5. CSS
6. Javascript




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
- Android 5.x以上のChrome



# ディレクトリ構成



### 基本的なディレクトリ構成
- 新規かつスタティックな中規模サイト構築時の例
```
root/
├index.html
├assets/
│　　　├css/
│　　　│ └ style.css
│　　　│
│　　　├img/
│　　　│ ├ index/
│　　　│ │　 └.jpg
│　　　│ └ category01/
│　　　│ 　 　└.jpg
│　　　└js/
│　　　　├jquery.js
│　　　　└common.js
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
　　　│  └.jpg
　　　│  └.png
　　　│ 　 
　　　└js/
　　　　├jquery.js
　　　　├page.js
　　　　└viewport.js
```



### ディレクトリ名使用文字
ディレクトリ名に使用できる文字は下記になります。

- 「a」～「z」までの小文字のアルファベット（1バイト）
- 「0」～「9」までの英数字（1バイト）
- 「-（ハイフン）」と「`_`（アンダースコア）」（いずれも1バイト）
- 先頭には「`-`（ハイフン）」「`_`（アンダースコア）」を使用しない。
- スペースは使用しない。




# HTML



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

#### Windows
- 改行コード　CR+LF(Windows標準の改行コード)

#### Mac or Linux
- 改行コード　LF


#### 文字コード
- UTF-8


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



## HTML書式ルール



### マークアップ全般
文書構造に適したマークアップを行います。
また、目的に応じた要素（タグ）を使用します。たとえば、見出しには見出し要素、段落にはp要素、アンカーにはa要素などを使用します。

```
<!-- 推奨 -->
<h2>見出しテキスト</h2>
<a href="recommendations/">All recommendations</a>

<!-- 非推奨 -->
<p>見出しテキスト</p>
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
「width=～」「height=～」は記述しません。サイズ変更はスタイルシートで行います。

```
<!-- 推奨 -->
<img src="sample.jpg" alt="サンプル画像">

<!-- 非推奨 -->
<img src="sample.jpg" width="200" height="100" alt="">
 ```


### 画像の命名規則
画像の命名は以下を原則とします。  
[ページ名・カテゴリ名] + [`_`] + ( [詳細] + [`_`] + ) [識別名]+ [連番2桁].拡張子  

```
<!-- 例 -->
about_feature_fig01.jpg
top_header_icon01.png
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
<!-- 推奨：レスポンシブ or　PCのみの場合 -->
<head>

<link rel="canonical" href="http://www.example.com/">

</head>

<!-- 推奨：PCSPセパレートの場合 -->
<head>

<link rel="canonical" href="http://www.example.com/">
<link rel="alternate" media="only screen and (max-width: 767px)" href="http://www.example.com/sp/" />

</head>

```


### 絶対パスによる記述
TOPへのリンクは案件に準じる形で記述します。
ルート相対パス及び相対パスの使用も可とします。
ただし、サイトリニューアルなどの際は絶対パスによる記述を推奨とします。

```
<!-- 推奨 -->
<a href="https://www.example.com">トップページ</a>

<!-- 可 -->
<a href="/">トップページ</a>
<a href="../">トップページ</a>
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



### 画像要素のalt属性
alt属性にて画像の代替となるテキストを設定します。  
altの内容について特に指定がない場合はコーダーの判断で画像の簡易説明を設定します。  
また、適切な代替内容が存在しない画像の場合は空のalt属性を設置します。

```
<!-- 推奨 -->
<img src="sample.jpg" alt="サンプル画像">

<!-- 非推奨 -->
<img src="sample.jpg">

<!-- 可 -->
<img src="sample.jpg" alt="">

 ```





### 画像圧縮について
画像圧縮はサイト表示速度改善に影響が大きいため  
デザインからスライスした画像を下記ツールを使用し、圧縮します。  
[compressor.io](https://compressor.io/)

特にサイズが大きい画像（メインビジュアルなど）については圧縮を必須とします。



### Webフォントについて
Webフォントを使用する場合、指定がない限りはGoogle fontsからの使用を推奨します。  
また、表示速度を考慮し、特に指定がない場合はCDNでの読み込みとします。





# CSS



### 文字コード
HTMLに合わせて記述します。原則UTF-8を使用。



### ID・Class名
原則、意味のある名前を設定します。
また、クラス名・ID名の最初の文字に数字を使わないでください。

#### Class
Class名には`-`で要素名を繋ぐケバブケースを使用します。  
プロジェクトよってBemなどの命名設計を使用する場合は`_`の使用も可。

```
<!-- 推奨 -->
<p class="body-copy">ダミーテキスト</p>

<!-- 非推奨 -->
<p class="bodyCopy">ダミーテキスト</p>
```



### ID・Classの使い分け
IDはスタイル指定には使用しません。
アンカーリンクの対象となる要素を除き、原則としてClassのみを使用してコーディングしてください。  
アンカーリンクの対象となる要素に関しても、通常通りにClassでスタイルを付与した後に、アンカーリンク用としてIDを付与して下さい。



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



### CSSコメントの挿入
ソース内容が把握しやすいよう、CSSにも必ずコメントを記述します。  
スタイルを当てているHTMLブロック、またはコンポーネントの名称を大タイトルとし、  
更に特筆すべきコンポーネントがある場合はサブタイトルを記述します。  
記述位置はそれぞれ対象スタイルの前行とします。

```
<!-- コメント記述例 -->

/*---------------------------------------------------------
header (大タイトル)
---------------------------------------------------------*/
.header {
    width: 100%;
}

/*global-navi　（サブタイトル）
--------------------------------------------------*/
.global-navi {
    width: 100%;
}

/*---------------------------------------------------------
layout (大タイトル)
---------------------------------------------------------*/
.flex {
    display: flex;
}

.l-col2 {
    width: 49%;
}
```



# Javascript



### 記述場所の前提
メンテナンス性を考慮し、スクリプトは原則外部ファイル化します。  
また、読み込み位置は</body>直前とします。
</body>直前に計測タグがある場合はその前に記述してください。

```
<!-- 推奨 -->
    <script src="/assets/js/common.js"></script>
</body>
```



### 文字コード
HTMLに合わせて記述します。原則UTF-8を使用。  
ただし、プラグインなどダウンロードして使用するものについては変更しません。



### document.write
document.writeは原則使用しません。



### jQuery
jQueryを使用する場合は2.x系安定バージョンの使用を推奨します。  
ただし、要件によっては1.x系を使用する場合があります。  
また、表示速度を考慮し、特に指定がない場合はCDNでの読み込みとします。

```
<!-- 推奨 -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.4/jquery.min.js"></script>
</body>
```


