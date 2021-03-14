# FAV_SHOPS 〜いつものお店のあの商品〜

## 概要
このアプリは、食材、消耗品、ファッション、ドラッグストアなど、さまざまなお店の商品をお気に入りできます。また購入場所や価格などのメモもできます。

- 「この前買った洋服、よかったけどどこで買ったか場所が思い出せない..」
- 「xxで買った洗剤が安かったけど、どこで買ったっけ？」

そんな悩みを解決するための簡単なアプリです。

## 解決策として
- いつものなじみのお店をお気に入り登録して好きな商品をお気に入りできるようにする。
- GoogleMapAPIを使用して位置情報もわかるようにする。
- 複数のお店、複数のジャンルでお気に入り登録できるようにする。
- 買い物リストの記入場所を用意し、過去に当てはまるものがあればそれを表示する。(検索結果に近い機能)

# テーブル設計(仮)

## usersテーブル

| Column             | Type    | Options                   |
| ------------------ | ------- | ------------------------- |
| nickname           | string  | null: false               |
| email              | string  | null: false, unique: true |
| encrypted_password | string  | null: false               |

### Association
- has_many :shops

## shopsテーブル
| Column    | Type       | Options                      |
| --------- | ---------- | ---------------------------- |
| shop_name | string     | null:false                   |
| user      | references | null:false, foreign_key: true|
| card      | references | null:false, foreign_key: true|

### Association
- has_many :users
- belongs_to :card

## itemsテーブル

| Column    | Type      | Options                      |
| --------- | -------   | ---------------------------- |
| item_name | string    | null:false                   |
| price     | integer   |                              |
| genre_id  | integer   | null:false                   |
| card      | references| null:false, foreign_key: true|

### Association
- belongs_to :shop