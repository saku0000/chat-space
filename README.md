# chat space db設計
## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|group|references|null: false, foreign_key: true|
|user|references|null: false, foreign_key: true|
- belongs_to :group
- belongs_to :user


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
|group_id|references|null: false, foreign_key: true|
|user_id|references|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false, index: true|
### Association
- has_many :messages
- has_many :groups_users
- has_many :groups, through: :groups_users