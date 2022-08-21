---
marp: true
paginate: true
theme: gaia
class:
  - lead
  - invert
---

<style>
p, h1, h2, h3, h4 {
  text-align: left !important;
}
</style>

# 良いAPIとは？真剣に考えてみる:thinking:

---

## API設計難しいと思いませんか？
## 正直、自分は苦手です……

---

# API設計に関してここで再度考える **きっかけ** になればと思います🙌

---
<style scoped>
p {
  font-size: 46px;
}
</style>

**[Web API The Good Parts](https://www.oreilly.co.jp/books/9784873116860/)** の書籍に **めちゃくちゃ影響** を受けているためこの書籍の内容が大量に出てきます:bow:

![width:80% bg right:40%](https://www.oreilly.co.jp/books/images/picture_large978-4-87311-686-0.jpeg)

---

# なぜ？良いAPIを設計するべきなのか？

---

<style scoped>
h3 {
  color: red;
}
</style>

# それは……
### なぜ？コードを **カッチョ良く** 書かなければならないのかという問と同じである！

---

# では良いAPIは何が嬉しいの？
# 良いAPIの定義を見ていきます

---
<style scoped>
h1:nth-child(2) {
  color: red;
}
</style>

# 良いAPIとは？
# **使いやすく**、**変更しやすく**、**セキュリティに強く**、**恥ずかしくない**

---

# 良いAPIとは？ - 使いやすい

**多くの人に使ってもらうために使いやすくなければならない！**

---

# 良いAPIとは？ - 変更しやすい

**システムの成長が止まることはない……変更しやすい設計でなければならない！**

---

# 良いAPIとは？ - セキュリティに強い

**APIにセキュリティリスクがあるようでは誰も使わない！**

---

# 良いAPIとは？ - 恥ずかしくない

**APIの出来を見てサービスを開発している人の技術レベルが見られてしまうため我らはカッチョ良く設計しなくてはならない！**

---

# 具体的な設計方法を見ていきましょう
# ……とその前に
# 知っておいた方がよい **API設計思想** を見ていきましょう

---

### Netflix 社の API 担当エンジニアリングディレクターの Daniel Jacobson 氏より提唱されている考え方

- [The Future of API Design: The Orchestration Layer](https://thenextweb.com/news/future-api-design-orchestration-layer)

---

## LSUDs（large set of unknown developers）
## SSKDs（small set of known developers）

---

| 設計思想 | 公開範囲                                              | 考慮すべき点                                                       |
|:--------:|:------------------------------------------------------|:-------------------------------------------------------------------|
| LSUDs    | パブリックに API を公開するもの                       | さまざまなユースケースを想定してなるべく汎用的にしなければならない |
| SSKDs    | 自社サービスのAPIなどの特定の開発者に限られているもの | 特定の開発者にとって便利で使いやすいものにするべき 　　　　　　　　|

---

# LSUDs や SSKDs によって良いAPIの定義が変わってくる！

---
