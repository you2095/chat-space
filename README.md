# DB設計

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :groups, through: :groups_users
- has_many :groups_users
- has_many :messages

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unique:true|
|member_addition|string|null:false|

### Association
- has_many :users, through: :groups_users
- has_many :groups_users
- has_many :messages

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|integer|

### Association
- belong_to :user
- belong_to :group

## groups_usersテーブル

|Column|Type|Option|
|------|----|------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belong_to :group
- belong_to :user

