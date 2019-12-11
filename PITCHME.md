---

marp: true
title: Marp CLI example
description: Hosting Marp slide deck on the web
theme: gaia
paginate: true
_paginate: false

---


# <!--fit--> Github Actionsで
# <!--fit--> NuxtプロジェクトをS3へ自動デプロイする
<br>
<br>

### 森 早人


---

# 自己紹介 :tada:


### 経歴  :book:
- (2017) SIer にてCATVネットワークエンジニア

### 最近ハマっているもの:boom:
- Apex Legends
- Echo show 5 いじり

---

#  Github Actionsって？ :eyes:
<br>

### -  Github 提供のCI/CDツール
### -  GitHubから直接コードをビルド、テスト、デプロイ可能
### -  使用可能OSはUbuntu、Windows、MacOS 

<br>

参考：https://github.co.jp/features/actions


---

# 導入方法 :tada:

<br>

1. レポジトリのルートディレクトリに`/.github/workflow` ディレクトリを作成する
2. `/.github/workflow`配下に、actionsを定義したワークフローファイル(yml)を置く

---
```yml
## /.github/workflow/s3-deploy.yml
name: Upload to S3
on: # トリガーとなるアクションの名前。クーロンのように定期実行することも可能
  push:
    branches:
      - master
jobs: # 実行内容
  deploy:
    name: Build & Deploy
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master # masterブランチにチェックアウト
      - uses: actions/setup-node@master # Node.jsの実行環境を用意
        with:
          node-version: 10.x
      - run: npm install
      - run: npm run build
      - uses: actions/aws/cli@master # aws cliを使用
        env:
          AWS_ACCESS_KEY_ID: ${{ secrets.S3_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.S3_SECRET_ACCESS_KEY }}
        with:
          args: s3 sync dist/ s3://clagecloud-nuxt-project
```

---

# Demo :corn:

<br>

### S3へ自動デプロイしてみる流れ

1. S3のバケットの作成
2. IAMユーザーの作成
3. シークレットを、Githubに登録
4. ワークフローファイルを配置

---

# まとめ
<br>

## - サクッとCICDを導入できる
## - デプロイ以外にもいろいろできそう
## - 他のCIサービスと比較してみたい
