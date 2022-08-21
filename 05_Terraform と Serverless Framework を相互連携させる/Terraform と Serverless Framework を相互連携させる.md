---
marp: true
# theme: gaia
_paginate: false
style: |
    p, h1, h2, h3, h4 { text-align: left; }
    section.delimiter { background: linear-gradient(25deg, yellow 30%,yellow 100px,white 100px,white 100%); }
    ul { list-style: none; }
    # div { border: solid; }
---

<!-- _class: delimiter -->

# Terraform と Serverless Framework を相互連携する

<div style="text-align: center;padding-top: 80px">
  <img src="./image/00_cooperation.png" />
</div>

<h2 style="text-align: right; margin-right: 4rem">Yuki Takagi</h2>

---

<div style="height: 100%">
  <h1>自己紹介</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  <div style="height: 80%; display: flex;justify-content: space-between; margin: 1rem;">
    <div style="width: 45%; background: url(https://scontent-nrt1-1.xx.fbcdn.net/v/t1.6435-9/119604723_3285085514901787_1350492750591504360_n.jpg?_nc_cat=111&ccb=1-7&_nc_sid=09cbfe&_nc_ohc=HmLep5LV4WoAX8Rw7VN&tn=T6b3UBCIVq3UemOD&_nc_ht=scontent-nrt1-1.xx&oh=00_AT9LfFhBMp6HJL0PEV4OBOodt0dhVG9kVuSD1IcR8Dit1g&oe=6326B72D) no-repeat top left; background-size: 100%"></div>
    <div style="width: 55%;">
      <!-- 名前 -->
      <p style="margin-left: 2rem;"><b>名前</b></p>
      <p style="margin-left: 4rem; margin-top: -1rem;">高木 勇気</p>
      <!-- エンジニア職 -->
      <p style="margin-left: 2rem;"><b>エンジニア職</b></p>
      <p style="margin-left: 4rem; margin-top: -1rem;">バックエンドエンジニア</p>
      <!-- アカウント -->
      <p style="margin-left: 2rem;"><b>Twitter, GitHub, Qiita, Zenn</b></p>
      <p style="margin-left: 4rem; margin-top: -1rem;">@dodonki1223</p>
      <!-- 所属 -->
      <p style="margin-left: 2rem;"><b>所属</b></p>
      <p style="margin-left: 4rem; margin-top: -1rem;">株式会社LegalForce</p>
      <!-- 所属 -->
    </div>
  </div>
</div>

---

<div style="height: 100%">
  <h1>自己紹介</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  <div  style="height: 100%; display: flex;justify-content: space-between;">
    <div style="width: 50%; background: url(./image/01_qiita.png) no-repeat top left; background-size: 63%"></div>
    <div style="width: 50%; background: url(./image/02_article.png) no-repeat top left; background-size: 90%"></div>
  </div>
</div>
