# README

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|mail|string|null: false|
|password|string|null: false|

### Association
- has_many :messages
- has_many :groups, through: :users_groups
- has_many :users_groups


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|
|image|text|
|users_id|references|null: false,foreign_key: true|
|group_id|references|null: false,foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :users, through: :users_groups
- has_many :messages
- has_many :users_groups

## users_groupテーブル
|Column|Type|Options|
|------|----|-------|
|users_id|references|null: false,foreign_key: true|
|group_id|references|null: false,foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
