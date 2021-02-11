# furima テーブル設計

## users テーブル

| Column    | Type   | Options     |
| --------- | ------ | ----------- |
| nickname  | string | null: false |
| email     | string | null: false |
| password  | string | null: false |
| name      | string | null: false |
| birth_day | date   | null: false |

### Association

- has_many :items
- has_many :comments
- has_many :addresses
- has_one :item_buys


## items テーブル

| Column       | Type      | Options                        |
| ------------ | --------- | ------------------------------ |
| item_name    | string    | null: false                    |
| image        | string    | null: false                    |
| category     | string    | null: false                    |
| state        | string    | null: false                    |
| area         | string    | null: false                    |
| shipping     | string    | null: false                    |
| shipping_day | string    | null: false                    |
| description  | text      | null: false                    |
| price        | integer   | null: false                    |
| user         | reference | null: false, foreign_key: true |

### Association

- belongs_tp :user
- has_many :comments
- has_one :item_buys


## comments テーブル

| Column  | Type      | Options                        |
| ------  | --------- | ------------------------------ |
| message | string    |                                |
| user    | reference | null: false, foreign_key: true |
| item    | reference | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :items


## item_buys テーブル

| Column    | Type      | Options                        |
| --------- | --------- | ------------------------------ |
| user      | reference | null: false, foreign_key: true |
| address   | reference | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :addresses


## addresses テーブル

| Column         | Type      | Options                        |
| -------------- | --------- | ------------------------------ |
| post_code      | integer   | null: false                    |
| prefectures    | date      | null: false                    |
| city           | string    | null: false                    |
| address        | string    | null: false                    |
| phone_number   | string    |                                |
| building       | string    |                                |
| user           | reference | null: false, foreign_key: true |

### Association

- belongs_to :item_buys
- belongs_to :users
