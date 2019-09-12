chat-space DB設計

## usersテーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false, index: true|
|Email|string|null: false, unique: true|
|password|string|null: false|
### Association
- has_many :massages
- has_many :groups, through: :users_groups
- has_many :users_groups

## groupsテーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false|
### Association
- has_many :messages
- has_many :users, through: :users_groups
- has_many :users_groups

## users_groupsテーブル
|Column|Type|Option|
|------|----|------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## messageテーブル
|Column|Type|Option|
|------|----|------|
|text|text||
|image|string||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
