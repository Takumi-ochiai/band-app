# テーブル設計

## users テーブル

| Column           | Type        | Options           |
| ---------------- | ----------- | ----------------- |
| nickname         | string      | null: false       |
| email            | string      | null: false       |
| password         | string      | null: false       |
| family_name      | string      | null: false       |
| first_name       | string      | null: false       |
| family_name_kana | string      | null: false       |
| area_id          | integer     | null: false       |
| city             | string      |                   |
| birthday         | date        |                   |
| part_id          | integer     | null: false       |
| introduction     | text        |                   |

### Association
- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## rooms テーブル

| Column           | Type        | Options           |
| ---------------- | ----------- | ----------------- |
| name             | string      | null: false       |

### Asociation
- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## room_users テーブル

| Column           | Type        | Options                        |
| ---------------- | ----------- | ------------------------------ |
| user             | references  | null: false, foreign_key: true |

### Association
- belongs_to :room
- belongs_to :user

## messages テーブル

| Column           | Type        | Options                         |
| ---------------- | ----------- | ------------------------------- |
| content          | string      |                                 |
| user             | references  | null: false, foreign_key: true  |
| room             | references  | null: false, foreign_key: true  |

### Association
- belongs_to :room
- belongs_to :user
