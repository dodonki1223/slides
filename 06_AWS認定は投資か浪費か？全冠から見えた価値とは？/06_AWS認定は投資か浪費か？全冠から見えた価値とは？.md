---
marp: true
theme: default
paginate: true
header: "AWS認定は投資か浪費か？ 全冠から見えた価値とは？"
footer: "@dodonki1223"

# スライドの説明書き
## center-slide
## top-slide
## aaaaaa
## aaaaaa

style: |
  section {
    background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
    font-family: 'Helvetica Neue', Arial, sans-serif;
  }

  /* center-slideの設定 */
  section.center-slide {
    display: flex;
    flex-direction: column;
    align-items: left;
    text-align: left;
    height: 100%;
  }
  section.center-slide h1 {
    width: 100% !important;
    box-sizing: border-box;
  }
  section.center-slide h2 {
    margin-top: 0 !important;
  }
  section.center-slide h3 {
    margin-top: 0 !important;
  }

  /* top-slideの設定 */
  section.top-slide {
    display: flex !important;            /* 明示的にflex（Marpの仕様に従う） */
    flex-direction: column !important;   /* 縦に並べる */
    justify-content: flex-start !important; /* 上詰め！ */
    align-items: flex-start !important;     /* 左寄せ（必要なら） */
    text-align: left !important;
    height: 100% !important;             /* スライドの高さを維持 */
  }
  section.top-slide h1 {
    width: 100% !important;
    box-sizing: border-box;
  }
  section.top-slide h2 {
    margin-top: 0 !important;
  }
  section.top-slide h3 {
    margin-top: 0 !important;
  }

  section.top-slide .content {
    display: flex;
    flex-direction: row;     /* 横並びにする */
    align-items: flex-start;
    justify-content: space-between;
    gap: 2em;
  }

  section.top-slide .content .text {
    flex: 1;
  }

  section.top-slide .content .image {
    flex: 1;
    text-align: right;
  }

  section.top-slide .content .image img {
    max-width: 65%;
    height: auto;
  }

  /* center-slide, top-slide両方の設定 */
  section.center-slide img,
  section.top-slide img {
    margin-top: 1em;
  }

  /* center-with-top-title の設定 */
  section.center-with-top-title {
    display: flex !important;
    flex-direction: column !important;
    justify-content: flex-start !important; /* 上にh1を置くため */
    height: 100% !important;
  }

  section.center-with-top-title .content {
    flex: 1;
    min-height: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;     /* 中央に表示 */
    align-items: flex-start;
    width: 100%;
    text-align: left;
  }

  section.center-with-top-title h1 {
    width: 100%;
    box-sizing: border-box;
  }

  h1 {
    color: #2c3e50;
    font-size: 1.8em;
    margin-bottom: 0.5em;
    border-bottom: 3px solid #3498db;
    padding-bottom: 0.2em;
  }
  h2 {
    color: #34495e;
    font-size: 1.5em;
  }
  h3 {
    color: #34495e;
    font-size: 1.3em;
  }
  ul {
    list-style-type: none;
    padding-left: 1.5em;
  }
  li {
    margin: 0.5em 0;
    position: relative;
  }
  li::before {
    content: "•";
    color: #3498db;
    font-weight: bold;
    position: absolute;
    left: -1em;
  }
  code {
    background: #f8f9fa;
    padding: 0.2em 0.4em;
    border-radius: 3px;
    font-family: 'Courier New', monospace;
  }
  blockquote {
    border-left: 4px solid #3498db;
    margin: 1em 0;
    padding-left: 1em;
    color: #7f8c8d;
  }
  img {
    max-width: 78%;
    height: auto;
    display: block;
    margin: 0em auto;
  }
  .image-reference {
    text-align: center;
    font-size: 0.8em;
    margin-top: 0em;
    color: #666;
  }
  .image-reference a {
    color: #3498db;
    text-decoration: none;
  }
  .image-reference a:hover {
    text-decoration: underline;
  }

  .name-tag {
    position: absolute;
    bottom: 1.5em;
    right: 2em;
    font-size: 1.5em;
    color: #555;
  }


---

<!-- _class: center-slide -->

# AWS認定は投資か浪費か？

## 全冠から見えた価値とは？

<div class="name-tag">Yuki Takagi</div>

---

<!-- _class: top-slide -->

# はじめに

<div class="content">

<div class="text">

- LOT に入社して3年と2ヶ月
- Backend, PEM
    - 最近は PM もかじっています
- LegalForce, LegalOn Cloud ではエディタを担当
    - エディタの初期メンバー
- 2024年12月から新プロダクトの方へ移動

</div>

<div class="image">

![me](./image/01_me.jpg)

</div>

---

<!-- _class: center-with-top-title -->

# はじめに

<div class="content">

## ここで質問があります！
## AWS認定の取得は投資ですか？それとも浪費ですか？
## あなたはどう考えますか？

</div>

---

<!-- _class: center-with-top-title -->

# はじめに

<div class="content">

## 最後にまた同じ質問をしますので考えてみてください。

</div>

---

<!-- _class: center-with-top-title -->

# はじめに

<div class="content">

## 今回の発表では皆さんがAWS認定について興味を持ったり取得しようと考えている人の参考になればと思っています！
## ところでお前はそんなにAWS認定について語れるのか？

</div>

---

<!-- _class: center-with-top-title -->

# はじめに

<div class="content">

## 安心して下さい！全部持っています！

</div>

---

<!-- _class: center-with-top-title -->

# はじめに


 ![all_certified](./image/00_All_Certified.png)

  <div class="image-reference">

  [認証バッジ一覧](https://www.credly.com/users/yuuki-takagi.3393fc26)

  </div>

---


<!-- _class: center-with-top-title -->

# はじめに

<div class="content">


## LOTに入社してからAWS認定を全冠したことで得られた価値について、今日はその経験を元に「AWS認定の取得は投資だったのか、浪費だったのか」一緒に考えていければと思います！
## また、これからAWS認定を取ろうかなと考えている方にとって、 少しでも参考になるような話ができればうれしいです！


</div>

---

<!-- _class: top-slide -->

# 目次

### 2. AWS認定の概要
### 3. 投資としての価値
### 4. 時間と費用の分析
### 5. キャリアへの影響
### 6. まとめ
