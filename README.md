# chat space db設計
## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
- belongs_to :groups
- belongs_to :users


## groupsテーブル
|Column|Type|Options| 
|------|----|-------|
|name|string|null: false,|
### Association
- has_many :groups_users
- has_many :messages
- has_many :users, through:  :groups_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :groups
- belongs_to :user

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many :messages
- has_many :groups_users
- has_many :groups, through:  groups_users