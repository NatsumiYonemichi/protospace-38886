# テーブル設計

## users テーブル

| Column             | Type   | Options     |
|------------------- | ------ | ----------- |
| email              | string | null: false |
| encrypted_password | string | null: false |
| name               | string | null: false |
| profile            | text   | null: false |
| occupation         | text   | null: false |
| position           | text   | null: false |

## Association

- has_many :comments
- has_many :prototypes

## prototypes テーブル

| Column             | Type       | Options     |
|------------------- | ------     | ----------- |
| title              | string     | null: false                    |
| catch_copy         | text       | null: false                    |
| concept            | text       | null: false                    |
| user               | references | null: false, foreign_key: true |

## Association

- belongs_to :users
- has_many :comments

## comments テーブル

| Column             | Type       | Options                        |
|------------------- | ---------- | ------------------------------ |
| content            | text       | null: false                    |
| prototype          | references | null: false, foreign_key: true |
| user               | references | null: false, foreign_key: true |

## Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column             | Type       | Options                        |
|------------------- | ---------- | ------------------------------ |
| content            | string     |                                |
| user               | references | null: false, foreign_key: true |
| room               | references | null: false, foreign_key: true |

- belongs_to :room
- belongs_to :user