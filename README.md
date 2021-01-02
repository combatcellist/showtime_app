# テーブル設計

## users テーブル

| Column             | Type    | Options      |
| ------------------ | ------- | ------------ |
| name               | string  | null: false  |
| profile            | text    | null: false  |
| profile-image      | string  | null: false  |
| email              | string  | unique: true |
| encrypted_password | string  | null: false  |

## Association
- has_many : diners
- has_many : comments


## diners テーブル

| Column             | Type         | Options                       |
| ------------------ | ------------ | ----------------------------- |
| name               | string       | null: false                   |
| diner-image        | string       | null: false                   |
| detail             | text         | null: false                   |
| user               | references   | null: false foreign_key :true |


## Association
- has_many   : diner_tags
- has_many   : comments
- belongs_to : user
- has_many   : tags, through: :diner_tags


## comments テーブル

| Column             | Type         | Options                       |
| ------------------ | ------------ | ----------------------------- |
| text               | text         | null: false                   |
| user               | references   | null: false foreign_key :true |
| diner              | references   | null: false foreign_key :true |


## Association
- belongs_to : user
- belongs_to : diner


## diner_tags テーブル

| Column             | Type         | Options                       |
| ------------------ | ------------ | ----------------------------- |
| user               | references   | null: false foreign_key :true |
| diner              | references   | null: false foreign_key :true |


## Association
- belongs_to : user
- belongs_to : diner


## tags テーブル

| Column             | Type         | Options                       |
| ------------------ | ------------ | ----------------------------- |
| tags               | text         | null: false                   |

## Association
- has_many   : diner_tags
- has_many   : diners, through: :diner_tags
