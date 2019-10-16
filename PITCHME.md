---

marp: true
title: Marp CLI example
description: Hosting Marp slide deck on the web
theme: gaia
paginate: true
_paginate: false

---


# <!--fit--> インフラテストを
# <!--fit--> うまくやりたい:rotating_light:



---

# 最近、"テスト"についてよく考える

<br>

### TDD、サバンナ、和田さん、、、
<br>

### ・・・インフラにもテストっていらないのかな？


---
# 新基盤  :tada:
<br>

## EC2インスタンスの構成管理にAnsible

## ➡「Fail-Fast」思想

---

# 「Fail-Fast」思想

<br>

## サーバの状態を設定できなかった段階で実行が失敗する
## = 成功したならば、宣言通りにサーバの状態がセットアップされていることが保証される
(あれ、テストいらないんじゃ)

---

# 不安をテストする
<br>


ーーーーーーーーーーーーーーーーーーーーーーーーーーーーー
#### - 開発中に「うまく動作するのか？」という不安
####  - => TDDで「不安のコントロール」をすることで解決
ーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

<br>

テスト駆動開発の勘違いを見直す : 圧倒亭グランパのブログ
http://at-grandpa.hatenablog.jp/entry/2018/01/15/022136


---
# サーバー構築での不安
<br>

## 1. Ansible での設定はうまくいってるか
## 2. とんでもない勘違いをしてないか
## 3. 完成をどう定義するか



---

# Testinfa
<br>


## ServerspecのPython版

## Ansible の機能や設定を使うことが可能

## [Testinfra](https://testinfra.readthedocs.io/en/latest/index.html)

---

# Demo

---

# まとめ
<br>

## インフラでも、
## 不安なく構築をすすめるため、
## テスト駆動開発するのもありかもしれない！