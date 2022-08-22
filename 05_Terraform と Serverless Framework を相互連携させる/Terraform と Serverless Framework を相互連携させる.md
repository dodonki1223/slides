---
marp: true
paginate: true
_paginate: false
style: |
    p, h1, h2, h3, h4 { text-align: left; }
    section.delimiter { background: linear-gradient(25deg, yellow 30%,yellow 100px,white 100px,white 100%); }
    ul { list-style: none; }
    # div { border: solid; }
---

<!--
AWS のハンズオン資料の「サーバーレスアーキテクチャで翻訳 Web API を構築する」（https://pages.awscloud.com/event_JAPAN_Hands-on-for-Beginners-Serverless-2019_Contents.html）を題材にしてハンズオンで作成したインフラをコード化していく流れを発表します。

主に以下のようなことを発表しようと思っています。
・コンソール画面で作成したインフラの一部を Terraformer(https://github.com/GoogleCloudPlatform/terraformer) を使ってコード化し体裁を整えながら再実装していった方法
・Terraform で作成したリソースを Serverless Framework で参照する方法
・Serverless Framework で作成したリソースを Terraform で参照する方法
-->

<!-- _class: delimiter -->

# Terraform と Serverless Framework を相互連携する

<div style="text-align: center;padding-top: 80px">
  <img src="./image/00_cooperation.png" />
</div>

<h2 style="text-align: right; margin-right: 4rem">Yuki Takagi</h2>

---

<!-- _class: delimiter -->

# 自己紹介

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

  <h3>最近の活動</h3>

  <div  style="height: 100%; display: flex;justify-content: space-between;">
    <div style="width: 50%; background: url(./image/01_qiita.png) no-repeat top left; background-size: 63%"></div>
    <div style="width: 50%; background: url(./image/02_article.png) no-repeat top left; background-size: 80%"></div>
  </div>
</div>

---

<!-- _class: delimiter -->

# 今日話すこと

---

<div style="height: 100%">
  <h1>今日話すこと</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  ## ふと Terraform と Serverless Framework はどうやって連携すればいいのか？という疑問を持ちました。

  ## そこで実際に試してみました 💪

  ## 今日は実際に試した結果、私が得た知見を発表したいと思います！
</div>

---

<!-- _class: delimiter -->

# アジェンダ

---

<div style="height: 100%">
  <h1>アジェンダ</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  <div style="padding-left: 2rem;">
    <h2 style="padding: 0;">1. 題材</h2>
    <h2 style="padding: 0;">2. Terraform と Serverless Framework で管理するもの</h2>
    <h2 style="padding: 0;">3. Serverless Framework を使ってコード化</h2>    
    <h2 style="padding: 0;">4. Terrafomer を使ってコード化</h2>
    <h2 style="padding: 0;">5. Serverless Framework → Terraform を連携する</h2>
    <h2 style="padding: 0;">6. Terraform → Serverless Framework を連携する</h2>
    <h2 style="padding: 0;">7. まとめ</h2>
  </div>
</div>

---

<div style="height: 100%">
  <h1>1. 題材</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  ### こんな感じのサーバーレスアーキテクチャを題材にします。

  <div>
    <img src="https://raw.githubusercontent.com/dodonki1223/image_garage/master/translate/00_overall.png" />
  </div>
</div>

---

<div style="height: 100%">
  <h1>1. 題材</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  ### こちらの構成は **AWS 初心者向けハンズオン** の「 **[サーバーレスアーキテクチャで翻訳 Web API を構築する](https://pages.awscloud.com/event_JAPAN_Hands-on-for-Beginners-Serverless-2019_Contents.html)** 」で作成する題材になります。

  <div style="text-align: center;">
    <img src="./image/03_hands_on.png" />
  </div>
</div>

---

<div style="height: 100%">
  <h1>1. 題材</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  ## **AWS 初心者向けハンズオン** の「 **[サーバーレスアーキテクチャで翻訳 Web API を構築する](https://pages.awscloud.com/event_JAPAN_Hands-on-for-Beginners-Serverless-2019_Contents.html)** 」は動画を10個見ながら言われたとおりにしていくだけで2時間もあれば簡単に実装することが出来ます。

  ## 私もこちらのハンズオンの終了後に Terraform と Serverless Framework を使って実装し直しました。

  ## 実装していった過程も含めて発表していきます！
</div>

---

<div style="height: 100%">
  <h1>アジェンダ</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  <div style="padding-left: 2rem;">
    <h2 style="padding: 0; color: gray;">1. 題材</h2>
    <h2 style="padding: 0;">2. Terraform と Serverless Framework で管理するもの</h2>
    <h2 style="padding: 0; color: gray;">3. Serverless Framework を使ってコード化</h2>
    <h2 style="padding: 0; color: gray;">4. Terrafomer を使ってコード化</h2>
    <h2 style="padding: 0; color: gray;">5. Serverless Framework → Terraform を連携する</h2>
    <h2 style="padding: 0; color: gray;">6. Terraform → Serverless Framework を連携する</h2>
    <h2 style="padding: 0; color: gray;">7. まとめ</h2>
  </div>
</div>

---

<div style="height: 100%">
  <h1>2. Terraform と Serverless Framework で管理するもの</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  <div style="text-align: center;">
    <img style="width: 68%" src="https://raw.githubusercontent.com/dodonki1223/image_garage/master/translate/01_relationship_between_terraform_and_serverless_framework.png" />
  </div>
</div>

---

<div style="height: 100%">
  <h1>2. Terraform と Serverless Framework で管理するもの</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  ## Terraform では **IAM ロール** と **AWS Systems Manager Parameter Store** の2つを管理します。

  ## 後に説明しますが **AWS Systems Manager Parameter Store** は Serverless Framework と連携するために必要になります。

  <div style="text-align: center;">
    <img style="width: 40%" src="https://raw.githubusercontent.com/dodonki1223/image_garage/master/translate/05_terraform_resources.png" />
  </div>
</div>

---

<div style="height: 100%">
  <h1>2. Terraform と Serverless Framework で管理するもの</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  ## Serverless Framework では **Amazon API Gateway** と **AWS Lambda** と **Amazon DynamoDB** と **CloudWatch Logs** の4つを管理します。

  <div style="text-align: center;margin-top: 6rem;">
    <img style="width: 80%" src="https://raw.githubusercontent.com/dodonki1223/image_garage/master/translate/06_serverless_framework_resources.png" />
  </div>
</div>

---

<div style="height: 100%">
  <h1>2. Terraform と Serverless Framework で管理するもの</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  ## Serverless Framework で管理しているリソースが多くない？

  ## Serverless Framework で多くのリソースを管理しているのは **ローカルの開発環境が整っている** ためです。

  ## **ローカルの開発環境で使用する必要があるのものは Serverless Framework で管理** し **それ以外は Terraform で管理する** ようにしています。
</div>

---

<div style="height: 100%">
  <h1>2. Terraform と Serverless Framework で管理するもの</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  ### ローカルにて実行と DynamoDB の操作ができます。

  <div style="text-align: center;">
    <img style="width: 80%" src="./image/04_local_development.png" />
  </div>
</div>

---

<div style="height: 100%">
  <h1>アジェンダ</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

  <div style="padding-left: 2rem;">
    <h2 style="padding: 0; color: gray;">1. 題材</h2>
    <h2 style="padding: 0; color: gray;">2. Terraform と Serverless Framework で管理するもの</h2>
    <h2 style="padding: 0;">3. Serverless Framework を使ってコード化</h2>
    <h2 style="padding: 0; color: gray;">4. Terrafomer を使ってコード化</h2>
    <h2 style="padding: 0; color: gray;">5. Serverless Framework → Terraform を連携する</h2>
    <h2 style="padding: 0; color: gray;">6. Terraform → Serverless Framework を連携する</h2>
    <h2 style="padding: 0; color: gray;">7. まとめ</h2>
  </div>
</div>

---

<div style="height: 100%">
  <h1>3. Serverless Framework を使ってコード化</h1>
  <p style="border-bottom: solid 5px #808080; margin-top: -2rem"></p>

</div>


# ここに Serverless Framework を使ったコード化方法を記載する
