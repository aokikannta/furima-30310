# DB 設計

## users table

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| email              | string              | null: false             |
| password           | string              | null: false             |
| nickname           | string              | null: false             |
| family_name        | string              | null: false             |
| first_name         | string              | null: false             |
| family_name_kana   | string              | null: false             |
| first_name_kana    | string              | null: false             |
| birth_day          | date                | null: false             |


### Association

* has_many :products dependent: :destroy
* belongs_to :destination dependent: :destroy
* belongs_to :card dependent: :destroy

## destination table

| Column                           | Type       | Options                        |
|----------------------------------|------------|-------------------------       |
| user_id                          | integer    | null: false, foreign_key: true |
| post_code                        | string     | null: false                    |
| prefecture_id                    | integer    | null: false                    |
| city                             | string     | null: false                    |
| address                          | string     | null: false                    |
| building_name                    | string     |                                |
| phone_number                     | string     |                                |


### Association

- belongs_to :product

## product table

| Column           | Type       | Options                        |
|------------------|------------|--------------------------------|
| name             | string     | null: false                    |
| price            | integer    | null: false                    |
| description      | string     | null: false                    |
| status_id        | integer    | null: false                    |
| size_id          | integer    | null: false                    |
| category_id	     | integer	  | null: false, foreign_key: true |
| brand_id         | integer	  | null: false, foreign_key: true |
| shipping_id      | integer	  | null: false, foreign_key: true |
| user_id	         | integer    | null: false, foreign_key: true |


### Association

- belongs_to :user dependent: :destroy

## brand table

| Column      | Type       | Options              |
|-------------|------------|----------------------|
| name        | string     | index: true          |


### Association

- has_many :products


