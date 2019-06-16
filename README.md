# README

## group_members中間テーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|text|null:false|

### Association
- has_many :messages
- has_many :users, through: :group_members # group_membersのuserからユーザー取得する
- has_many :group_members

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false,foreign_key:true|
|content|text|
|image|text|
|group_id|integer|null: false,foreign_key:true|

### Association
- belongs_to :group
- belongs_to :user

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|integer|null:false
|email|string|null: false|

### Association
- has_many :messges
- has_many :groups, through: :group_members # 自分で作ったグループ
- has_many :group_members
