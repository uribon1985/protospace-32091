# テーブル設計

## users テーブル

|   Column   |  Type  |  Options    |
| ---------- | ------ | ----------- |
| name       | string | null: false |
| email      | string | null: false |
| password   | string | null: false |
| profile    | text   | null: false |
| occupation | text   | null: false |
| position   | text   | null: false |

### Association

- has_many :comments
- has_many :prototypes, through: :comments

## prototypes テーブル

|   Column   | Type       |            Options             |
| ---------- | ---------- | ------------------------------ |
|   title    | string     | null: false                    |
| catch_copy | text       | null: false                    |
|  concept   | text       | null: false                    |
|   user     | references | null: false, foreign_key: true |

### Association

- has_many :comments
- has_many :users, through: :comments


## comments テーブル 

|   Column  | Type       |           Options              |
| --------- | ---------- | ------------------------------ |
|   text    | string     |                                |
|   user    | references | null: false, foreign_key: true |
| prototype | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :prototype
