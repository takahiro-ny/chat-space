chat-space DB設計

##usersテーブル
|Column|Type|Option|
|------|----|------|
|id|integer|null: false|
|name|string|null: false|
|Email|string|null: false, unique: true|
|password|string|null: false|
###Association
- has_many :massages
- has_many :groups, through: :users_groups
- has_many :users_groups

##groupsテーブル
|Column|Type|Option|
|------|----|------|
|id|integer|null: false|
|name|string|null: false|
###Association
- has_many :messages
- has_many :users, through: :users_groups
- has_many :users_groups

##users_groupsテーブル
|Column|Type|Option|
|------|----|------|
|id|integer|null: false|
|user_id|integer|null: false|
|group_id|integer|null: false|
###Association
- belongs_to :user
- belongs_to :group

##messageテーブル
|Column|Type|Option|
|------|----|------|
|id|integer|null: false|
|text|text|null: false|
|image|string|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
###Association
- belongs_to :user
- belongs_to :group
