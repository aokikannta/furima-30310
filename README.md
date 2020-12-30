# README
# DB 設計

## users table

| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| email              | string              | null: false, unique: true |
| encrypted_password | string              | null: false               |
| nickname           | string              | null: false               |
| family_name        | string              | null: false               |
| first_name         | string              | null: false               |
| family_name_kana   | string              | null: false               |
| first_name_kana    | string              | null: false               |
| birth_day          | date                | null: false               |


### Association

* has_many :products dependent: :destroy
* has_many :managements

## destination table

| Column                           | Type       | Options                        |
|----------------------------------|------------|-------------------------       |
| post_code                        | string     | null: false                    |
| prefecture_id                    | integer    | null: false                    |
| city                             | string     | null: false                    |
| address                          | string     | null: false                    |
| building_name                    | string     |                                |
| phone_number                     | string     | null: false                    |
| management_id                    | integer    | null: false, foreign_key: true |




### Association

- belongs_to :management

## product table

| Column           | Type       | Options                        |
|------------------|------------|--------------------------------|
| name             | string     | null: false                    |
| price            | integer    | null: false                    |
| description      | text       | null: false                    |
| status_id        | integer    | null: false                    |
| prefecture_id    | integer    | null: false                    |
| area_id          | integer    | null: false                    |
| state_id         | integer    | null: false                    |
| days_id          | integer    | null: false                    |
| user_id	         | integer    | null: false, foreign_key: true |


### Association

- belongs_to :user 
- has_one :management

## management table

| Column           | Type       | Options                        |
|------------------|------------|--------------------------------|
| user_id          | integer    | null: false, foreign_key: true |
| item_id          | integer    | null: false, foreign_key: true |


### Association

- belongs_to :user 
- belongs_to :product
- has_one :destination



