# README

# DB設計

## users table

|Column|Type|Options|
|------|----|-------|
| name | string | index: true, null: false |
| mail | string | null: false, unique: true |
| password | string | null: false |

### Association
- has_many :messages, through: :members
- has_many :members
- has_many :groups, through: :members


## messages table

|Column|Type|Options|
|------|----|-------|
| body | text | null: false, foreign_key: true |
| image | string | foreign_key: true  | 
| user_id | integer | null: false, foreign_key: true |
| group_id | integer | null: false, foreign_key: true |

### Association

- belongs_to :group
- belongs_to :user

## members table

|Column|Type|Options|
|------|----|-------|
| user_id | integer | null: false, foreign_key: true |
| group_id | integer | null: false, foreign_key: true |

### Association

- belongs_to :group
- belongs_to :user

## groups table

|Column|Type|Options|
|------|----|-------|
| user_id | integer | null: false, foreign_key: true |
| body | text | null: false, foreign_key: true |
| image | string | foreign_key: true |

### Association

- belongs_to :user
- has_many :messages through: :members

