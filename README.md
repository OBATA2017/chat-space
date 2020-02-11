# README

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false, unique: true|
### Association
- has_many :groups_users
- has_many :groups, through: :groups_users
- has_many :messages

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
### Association
- has_many :groups_users 
- has_many :users, through: :groups_users
- has_many :messages

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

<!-- references型とは、type=カラムの型であり、マークダウン表記の際は、typeの所に、integer(型)→references(型)と表記する？ -->
<!-- ①中間テーブルである「groups_users」を使用する際、integer型では、外部キーであるforeign_key: trueは外部制約にならない？ 
       故に、references型にする事で、外部キーであるforeign_key: trueは外部制約が適応される？-->
<!-- references型を使用する際は、テーブルが生成される時に自動に _id が付与されるため、カラム名は  user_id を user と記述する。
      また、references型を使用する事で、インデックス(テーブル内のデータの検索を高速にするための仕組み)を自動で作成してくれる。 -->

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|references|null: false, foreign_key: true|
|image|references|foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group