# README
キャラノベル（Chara-Novel）
# 概要
web小説を投稿する際、その小説の登場人物を記録しておくことができる。
また、登場人物の情報を作者は投稿画面で、読者は小説の本文画面にていつでも確認することができるアプリケーション。
# 本番環境

# 作成背景（意図）
web小説を投稿する際、小説に登場する多くの人物を管理、記録しておきたいと考えました。
これを管理することで、執筆者は過去の登場人物を遡って探す必要がないため、より執筆に時間を使うことができるよになります。
さらに、ネット上で情報を管理することで、いつでもどこでも執筆に取り組むことができます。
加えて、登場人物の記録は、読者が登場人物がどのような性格だったか？などを見直す際にも利用することができるため、
よりストーリーに集中することができます。
将来的には小説の名前やジャンルではなく、登場人物の画像などから小説に興味を持ってもらう、というような小説の発見の仕方を提供できたらと考えています。

# DEMO

## 〇〇画面

## 〇〇画面

## 〇〇画面

## 〇〇画面

## 〇〇画面

# 工夫したポイント

# 使用技術（開発環境）
## バックエンド
Ruby, Ruby on Rails
## フロントエンド
HTML, CSS, Javascript, jQuery, Ajax
## データベース
MySQL
## インフラ

# 課題や今後実装したい機能
## 課題
あらすじや本文のテキストの改行をできるようにすること。
## 実装したい機能
マイページ画面
小説へのコメント機能
小説のランキング機能
キャラクターのランキング機能
画像投稿機能

# DB設計
## usersテーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| user_name          | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association

- has_many :books
- has_many :pages
- has_many :chapters
- has_many :characters

## booksテーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| title              | string     | null:false                     |
| genre              | integer    | null:false                     |
| arasuji            | string     | null:false                     |
| status             | integer    | null:false                     |
| user               | references | null:false, foreign_key: true  |

### Association

- belongs_to :user
- has_many :pages
- has_many :chapters
- has_many :characters

## pagesテーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| page_title         | string     | null:false                     |
| text               | text       | null:false                     |
| user               | references | null:false, foreign_key: true  |
| book               | references | null:false, foreign_key: true  |

### Association

- belongs_to :user
- belongs_to :book
- belongs_to :chapter

## chapterテーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| chapter_title      | string     | null:false                     |
| user               | references | null:false, foreign_key: true  |
| book               | references | null:false, foreign_key: true  |
| page               | references | null:false, foreign_key: true  |

### Association

- belongs_to :user
- belongs_to :book
- has_many :pages

## charactersテーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| chara_name         | string     | null:false                     |
| sex                | integer    | null:false                     |
| age                | string     | null:false                     |
| chara_text         | text       | null:false                     |
| user               | references | null:false, foreign_key: true  |
| book               | references | null:false, foreign_key: true  |

### Association

- belongs_to :user
- belongs_to :book

## ER図
[![Image from Gyazo](https://i.gyazo.com/d0a5f554fb7bc0547c62f18b0dff838b.png)](https://gyazo.com/d0a5f554fb7bc0547c62f18b0dff838b)