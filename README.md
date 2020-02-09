# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# README.md

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, funique: true|
|name|integer|null: false, funique: true|
|email|string|null: false, funique: true|
|password|string|null: false, funique: true|
### Association
- has_many :groups
- has_many :groups, through: :groups

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false, funique: true|
|group_name|integer|null: false, funique: true|
|member|integer|null: false, funique: true, foreign_key: true|
### Association
- has_many :users 
- has_many :users, through: :users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|message_id|integer|null: false, funique: true|
|user_id|integer|null: false, foreign_key: true|
|tweet_id|integer|null: false, foreign_key: true|
|body|text|null: false, foreign_key: true|
|image|string|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group