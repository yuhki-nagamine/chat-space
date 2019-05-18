# README

# DB設計

## users table

|Column|Type|Options|
|------|----|-------|
| name | string | index: true, null: false |
| mail | string | null: false, unique: true |
| password | string | null: false |

### Association
- has_many :messages
- has_many :members
- has_many :groups, through: :members


## messages table

|Column|Type|Options|
|------|----|-------|
| body | text | 
| image | string | 
| user_id | references | null: false, foreign_key: true |
| group_id | references | null: false, foreign_key: true |

### Association

- belongs_to :group
- belongs_to :user

## members table

|Column|Type|Options|
|------|----|-------|
| user_id | references | null: false, foreign_key: true |
| group_id | references | null: false, foreign_key: true |

### Association

- belongs_to :group
- belongs_to :user

## groups table

|Column|Type|Options|
|------|----|-------|
| name | string | null: false |

### Association

- has_many :users
- has_many :messages through: :members
- has_many :members 

