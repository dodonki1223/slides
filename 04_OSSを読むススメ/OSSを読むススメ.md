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

# OSSを読むススメ

---

## なぜOSSを読むのか？

- #### コードを書いている時 **「どういうふうに書くのが良いのだろうか？」** と考えたことは無いでしょうか？

- #### 書けるんだが **本当にこの書きぶりでいいのだろうか** と思ったことは無いでしょうか？

- #### 自社のプロダクトコードに **参考になるコードが無い！？**

---

# **そんな時こそ OSS を読もう！**

---

## OSSを読むことによって解決すること

- #### こういう時は **どのようにして書いたら良いんだろうか？**

- #### 一般的には **どのように実装するのだろうか？**

- #### なんか書けたけど **もっとDryに書けるのではないだろうか？**

- #### 自社のプロダクトに **参考になるコードがない！？**  どうしよう……


---

<style scoped>
img {
  width: 75%;
}
div {
  margin: 0 auto;
}
</style>


# OSS 最高

<div>
  <p>
    <img src="https://4.bp.blogspot.com/-zTvzECyWEsk/VwIjHWMdszI/AAAAAAAA5e4/W_kAnVythXoHGzGO3AkgrHImS3cpvMiuQ/s800/internet_kanki_man1.png"></img>
  </p>
</div>

---

# ちょっと待って！

# Qiita や Zenn の記事では駄目なの？

---

## Qiita や Zenn の記事では駄目なの？

- #### 記事が書かれた **時期によって参考にすべきかどうか** を考えないといけません

- #### **アプリケーションは日々進化している** ため、**数年前の記事はもう使えないものになっている** かもしれません

- #### OSSのコードは日々進化していて **最新を追従していることが圧倒的に多い**

- #### なんだかんだ言って **公式ドキュメントが最強** である

---

# いい記事もいっぱいあるので

# 自分で **取捨選択**して

# **Qiita や Zenn の記事**も参考にしてね👀

---

<style scoped>
img {
  width: 70%;
}
</style>

### 例えばこの人の記事は
### とても参考になります

![width:95% bg right:50%](./image/qiita_dodonki1223.png)

---

<style scoped>
h3 {
  margin-left: 40px;
}
</style>

## 自分が参考にする記事

### 1. 公式ドキュメント

### 2. OSS

### 3. 英語の記事

### 4. Qiita、Zenn

---

# 皆さんは **何を参考** にしますか？

---

## OSS の読み方

- #### 1つのプロジェクトだけでなく **複数のプロジェクトを参考** にする

- #### OSS同士で **似たような書きぶり** があるのでそれを参考にする

- #### 中身を理解しようとするのではなく **書きぶりを見る**

---

## なぜ書きぶりを見るの？

#### OSSを読んでいて自分はよくあることなんですが **読んでも理解できないこと**があります😭

#### これは完全に自分の実力不足もあるんですが 処理をする時の**前提条件などはOSSで把握する**には時間がかかります……

#### なので中身を理解しようとせずに **書きぶりに注力します！**

---

## なぜ書きぶりを見るの？

### 書きぶりを元にGoogleで検索することで **理解が深まります**

---

### **なんだこのメソッドは🤔**

⬇

### **Google検索**

⬇

### **おぉ！そんなものがあったのか😮**

みたいな気付きがよくありました！
中身を理解できる方は理解した上で読むと良いと思います！

---

## 実際にRailsのOSSを読んでみる

**2022/04/25 時点の情報**ですので古い可能性があります。

| リポジトリ                                          | Rails             |  Ruby                    | star   |
|:---------------------------------------------------:|:-----------------:|:------------------------:|:------:|
| [forem](https://github.com/forem/forem)             | 7.0.2.3           | 3.0.2                    | 18,982 |
| [gitlabhq](https://github.com/gitlabhq/gitlabhq)    | 6.1.4.7           | 2.7.4                    | 22,890 |
| [huginn](https://github.com/huginn/huginn)          | 6.0.4.4           | 2.6.5                    | 35,447 |
| [postal](https://github.com/postalhq/postal)        | 5.2.6.2           | 2.6.9                    | 11,542 |
| [mastodon](https://github.com/tootsuite/mastodon)   | 6.1.5             | 3.0.3                    | 27,613 |
| [discourse](https://github.com/discourse/discourse) | 最新              | 2.7.2以上                | 33,541 |
| [spree](https://github.com/spree/spree)             | 6.1 or 6.0 or 5.2 | 2.5 or 2.6 or 2.7 or 3.0 | 11,784 |

---

## before_destroy を調べてみる

以前、ある機能改修でのことです  
後輩に **before_destroy** を使用しましたと報告を受けました

ただ自分が **before_destroy** を使用したことがなかったのでこの **Active Record コールバック** は一体どういう時に使うべきなのだろうか……と思い調べてみました

---

### 単純に検索してみる

Googleで検索してみるとTOPには model の削除可否チェックが出てきています

![width:90% bg right:50%](https://raw.githubusercontent.com/dodonki1223/image_garage/master/articles/17/01_search_before_destroy_for_google.png)

---

### foremで検索してみる

cache と名の付くメソッドを実行していることが多いようです  
メソッド名から察するにデータの削除と一緒にキャッシュに対して何かを行うようなことが多そうです  

![width:90% bg right:50%](https://raw.githubusercontent.com/dodonki1223/image_garage/master/articles/17/02_search_before_destroy_for_github.png)

---

## Google検索と比べてみましたが**検索結果が全然違い**ます

## もしGoogleでのみ検索していた場合は**削除可否に使う**のかと思ってしまってもおかしくないですね

---

## ここで問題が……

#### 本来なら**複数の OSS から before_destory を検索したい**と思いますよね

#### ただ GitHub の検索機能だとそれぞれの OSS から検索しないといけないため**すごく非効率**です……

#### そんなことでお困りのあなたに**私が行っている検索方法を共有**しようと思います！

---

### VS Code のワークスペース機能を使用して検索する

そもそもワークスペースとは？
公式ドキュメントには以下のように書かれています

> A Visual Studio Code "workspace" is the collection of one or more folders that are opened in a VS Code window (instance). In most cases, you will have a single folder opened as the workspace but, depending on your development workflow, you can include more than one folder, using an advanced configuration called Multi-root workspaces.

出典：[What is a VS Code "workspace"?](https://code.visualstudio.com/docs/editor/workspaces)

---

#### ウィンドウに**複数のルートフォルダを開ける**ようにする機能です

#### 複数の OSS をワークスペースに追加すると以下のような感じになります

![width:95% bg right:50%](https://raw.githubusercontent.com/dodonki1223/image_garage/master/articles/17/03_workspace.png)

---

![width:75% bg right:50%](https://raw.githubusercontent.com/dodonki1223/image_garage/master/articles/17/04_search_workspace.png)

#### 実際に **before_destory** をワークスペースで検索してみると以下のようになります

#### 複数の OSS から検索できるようになりました！ **おめでとうございます！**

---

# 今日の発表を終わります

---

# ……

---

<style scoped>
img {
  width: 65%;
}
div {
  margin: 0 auto;
}
</style>

# うん！？ ちょっと待って！

<div>
  <p>
    <img src="https://3.bp.blogspot.com/-VkaXRdIAzRU/WUdYwLM2msI/AAAAAAABE_E/Ob4pV2KxYAUvnkvQDhtTdY-lWeZWWbTkACLcBGAs/s800/kaisya_komaru_man.png"></img>
  </p>
</div>

---

## ローカルにそれぞれの **OSS を git clone** してきてそれをワークスペースに設定するの**めんどくさくない？**

## **OSS が更新**したらどうすりゃいいんや……

---

## そんなことを思った**そこのあなた！**

## 大丈夫です！ **もっと簡単に取得できる**ようにしましょう！

---

# 私が以前、簡単にOSSを clone & update できるツールを作成しました〜

---

Rails に関しては [rails_oss](https://github.com/dodonki1223/rails_oss) リポジトリを clone してきて

**bash clone_and_update.bash** を実行するだけで簡単にローカルに検索できる環境が出来上がります

![width:90% bg right:50%](https://raw.githubusercontent.com/dodonki1223/image_garage/master/articles/17/05_rails_oss_project.png)

---

## リポジトリの clone と update が終わった後は 

## **oss.code-workspace** ファイルを開き **cmd + shift + f** で検索したい文字を打てば検索できるようになります

---

## このツールは設定された OSS を clone ＆ update し自動でワークスペースファイルを作成するツールになります

---

## 動作させると以下のような感じで自動で clone と update が行われるようになります

![width:90% bg right:50%](https://raw.githubusercontent.com/dodonki1223/image_garage/master/articles/17/06_sample_run_rails_oss.png)

---

## clone_and_update.bash が

## 何をやっているか説明していきます

---

```bash
#!/bin/bash

declare -a cloneList=($(cat ./list/ssh))

echo '{
	"folders": [' > oss.code-workspace

for ((i = 0; i < ${#cloneList[@]}; i++)) {
  project_name=$(echo "${cloneList[i]}" | cut -d '/' -f2 | sed -e 's/.git//g')
  project_dir="./${project_name}"

  echo '		{
			"path": "'${project_name}'"
		},' >> oss.code-workspace

  if [ ! -d $project_dir ]; then
    echo $project_name clone start...
    git clone ${cloneList[i]}
  else
    echo $project_name clone skip...
    echo $project_name update
    cd $project_name
    git fetch
    git pull
    cd ../
  fi
}

echo '	],
	"settings": {}
}' >> oss.code-workspace
```

---

<style scoped>
pre {
  font-size: 33px;
}
</style>

### clone ＆ update するリポジトリのリストを取得する

./list/ssh にリポジトリのリストが書かれており以下のコマンドでリストを取得します

```bash
declare -a cloneList=($(cat ./list/ssh))
```

./list/ssh には以下のようにリストを設定しています

```
git@github.com:forem/forem.git
git@github.com:gitlabhq/gitlabhq.git
git@github.com:huginn/huginn.git
git@github.com:postalhq/postal.git
git@github.com:tootsuite/mastodon.git
git@github.com:discourse/discourse.git
git@github.com:spree/spree.git
```

---

<style scoped>
pre {
  font-size: 17px;
}
</style>

### clone & update を行う

./list/ssh で取得したリスト分、繰り返し処理を行います  
フォルダが存在してなければ clone を行い、フォルダが存在していれば update を行います

```bash
# ./list/ssh に追加したリポジトリ分繰り返す
for ((i = 0; i < ${#cloneList[@]}; i++)) {
  # git@github.com:oss_name/oss_name.git の形式からプロジェクト名を取得
  project_name=$(echo "${cloneList[i]}" | cut -d '/' -f2 | sed -e 's/.git//g')

  # プロジェクトのフォルダパスを取得
  project_dir="./${project_name}"

  # プロジェクトのディレクトリが存在するか
  if [ ! -d $project_dir ]; then
    # プロジェクトが存在しない場合は git clone を実行する
    echo $project_name clone start...
    git clone ${cloneList[i]}
  else
    # プロジェクトが存在している場合は git fetch & git pull を行う
    echo $project_name clone skip...
    echo $project_name update
    cd $project_name
    git fetch
    git pull
    cd ../
  fi
}
```

---

<style scoped>
pre {
  font-size: 19px;
}
</style>

### ワークスペースファイルを自動生成する

./list/ssh ファイルに記載されている git clone 用の URL からワークスペースのファイルを自動生成します

```bash
  ・
  ・
  ・
echo '{
	"folders": [' > oss.code-workspace
  ・
  ・
  ・
for ((i = 0; i < ${#cloneList[@]}; i++)) {
  ・
  ・
  ・
  echo '		{
			"path": "'${project_name}'"
		},' >> oss.code-workspace
  ・
  ・
  ・
}

echo '	],
	"settings": {}
}' >> oss.code-workspace
```

---

## 新しく OSS を追加する

#### 新しく OSS を追加したい場合は ./list/ssh ファイルに **git clone の URL を追加** します

#### ./list/ssh ファイルに追加するだけで**ワークスペースファイルも更新される**ので特に気にする必要はありません

---

# 素敵なOSSライフを！

# 今日の発表を終わります
