# コーディングルール草稿

---

## インデックス

1. 本規約の目的と方針
2. 対象ブラウザ
3. レスポンシブデザインの方針
4. 開発情報の確認
5. 対象言語
6. HTML
7. CSS
8. Javascript


---

## 本規約の目的と方針
---
### 方針
- 運用・拡張していく上で破綻が起きづらい全体設計
- 担当者が変わっても編集・変更しやすい技術選定
- コンポーネント指向を意識し再利用可能なソースを目指す

---

### 目的
- 納品物（Webサイトデータ）に一定の品質を担保する

---

# 対象言語

- HTML
- CSS
- Javascript

---

# HTML

---

## スタイルの基本ルール

---

#### HTTPSプロトコル
可能な限り、埋め込みリソースにはHTTPSプロトコルを使用する。  
それぞれのファイルがHTTPS上で利用不可の場合を除き、画像やその他メディアファイル、スタイルシート、およびスクリプトには常にHTTPSプロトコル（https://)を使用する。

```
<!-- 推奨 -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

<!-- 可：プロトコルを省略（状況により使用可） -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

<!-- 非推奨：HTTPプロトコルを使用 -->
<script src="http://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>

```

---

## 書式の基本ルール

---

#### インデント
インデントはスペース4つとし、タブを使用したり、タブとスペースを混在させたりしない。

```
<ul>
    <li>Fantastic</li>
    <li>Great</li>
</ul>
```

---

#### 大文字・小文字の使用
小文字のみを使用するようにする。  
HTML要素名、属性、属性値（text/CDATAを除く）、CSSセレクタ、プロパティ、およびプロパティ値（文字列を除く）は小文字を使用する。

```
<!-- 推奨 -->
<img src="google.png" alt="Google">

<!-- 非推奨 -->
<A HREF="/">Home</A>
```

---

## HTMLスタイルルール

---

#### ドキュメントタイプ
HTML5を使用する。HTML5（HTML構文）は、すべてのHTML文書で優先される。

---

#### タイプ属性
スタイルシートとスクリプトのtype属性は省略する。CSSとJavaScriptには型属性を使用しない。  
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

#### 一行一要素
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

#### HTMLクォーテーション（引用符）
属性値を引用するときは、ダブルクォーテーション（二重引用符）を使用する。  
属性値の前後にはシングルクォーテーション（ ' ）ではなく、ダブルクォーテーション（ " ）を推奨する。
```
<!-- 推奨 -->
<a class="maia-button maia-button-secondary">Sign in</a>

<!-- 非推奨 -->
<a class='maia-button maia-button-secondary'>Sign in</a>
 ```
---
