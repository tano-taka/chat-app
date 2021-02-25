# テーブル設計

## users テーブル

| Column   | Type        | 0ptions          |
| ------   | ----------- | ---------------- |
| name     | string      | null: false      |
| email    | string      | null: false      |
| password | string      | null: false      |

### Association

- has_meny :room_users
- has_meny :rooms, through: room_users
- has_meny :messages

## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_meny :room_users
- has_meny :users, through: room_users
- has_meny :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :room

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :room
