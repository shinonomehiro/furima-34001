# furima テーブル設計

## users テーブル

| Column          | Type   | Options                  |
| --------------- | ------ | ------------------------ |
| nickname        | string | null: false              |
| email           | string | null: false, unique: true|
| password        | string | null: false              |
| first_name      | string | null: false              |
| last_name       | string | null: false              |
| first_name_kana | string | null: false              |
| last_name_kana  | string | null: false              |
| birthday        | string | null: false              |

### Association

- has_many :items
- has_many :orders
- has_one :addresses


## items テーブル

| Column        | Type      | Options                        |
| ------------- | --------- | ------------------------------ |
| item_name     | string    | null: false                    |
| text          | string    | null: false                    |
| category      | string    | null: false                    |
| condition     | string    | null: false                    |
| shipping_cost | string    | null: false                    |
| shipping_day  | string    | null: false                    |
| prefectures_  | integer   | null: false                    |
| price         | integer   | null: false                    |
| user_id       | reference | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :orders


## orders テーブル

| Column       | Type      | Options                        |
| ------------ | --------- | ------------------------------ |
| user_id      | reference | null: false, foreign_key: true |
| item_id      | reference | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :items
- has_one :addresses


## addresses テーブル

| Column          | Type      | Options                        |
| --------------- | --------- | ------------------------------ |
| post_code       | string    | null: false                    |
| city            | string    | null: false                    |
| address         | string    | null: false                    |
| building        | string    |                                |
| phone_number    | string    |                                |
| prefectures_    | integer   | null: false                    |
| user_id         | reference | null: false, foreign_key: true |

### Association

- belongs_to : users
- belongs_to : orders
