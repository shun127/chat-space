# README

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|mail|string|null: false|
|password|string|null: false|

### Association
- has_many :messages
- has_many :group, through: :users_group
- has_many :users_group


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|text||
|users_id|references|null: false,foreign_key: true|
|group_id|references|null: false,foreign_key: true|

### Association
- belongs_to :user
- belongs_to :groups

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|users_id|references|null: false,foreign_key: true|
|group_id|references|null: false,foreign_key: true|

### Association
- has_many :users, through: :users_group
- has_many :messages
- has_many :users_group

## users_groupテーブル
|Column|Type|Options|
|------|----|-------|
|users_id|references|null: false,foreign_key: true|
|group_id|references|null: false,foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
