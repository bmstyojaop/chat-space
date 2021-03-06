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

# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|password|string|null: false|
|email|string|null: false|
### Association
- has_many :messages
- has_many :groups_users
- has_many :groups, through: group_users

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :messages
- has_many :groups_users
- has_many :users, through: group_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key|
|group_id|integer|null: false, foreign_key|
### Association
- belong_to :user
- belong_to :group

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|content|string||
|image|strong||
|user_id|integer|null: false, foreign_key|
|group_id|integer|null: falser, foreign_key|
### Association
- belong_to :user
- belong_to :group