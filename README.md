## usersテーブル

|Column             |Type     |Options               |
|nikname            |string   |null:false            |
|email              |string   |null:false,unique:true|
|encrypted_password |string   |null:false            |
|family_name        |string   |null:false            |
|first_name         |string   |null:false            |
|family_name_kana   |string   |null:false            |
|first_name_kana    |string   |null:false            |
|birthdate          |date     |null:false            |

### Association
・has_many :items, dependent: :destroy, foreign_key: :items
・has_many :order, dependent: :destroy

## itemsテーブル

|Column       |Type      |Options                     |
|name         |string    |null:false                  |
|text         |text      |null:false                  |
|category_id  |integer   |null:false                  |
|condition_id |integer   |null:false                  |
|postage_id   |integer   |null:false                  |
|prefecture_id|integer   |null:false                  |
|prepare_id   |integer   |null:false                  |
|price        |integer   |null:false                  |
|user         |references|foreign_key:true            |


### Association
・belongs_to :user
・has＿one：order


### addressesテーブル

|Column          |Type      |Options                       |
|post_code       |string    |null:false                    |
|prefecture_id   |integer   |null:false                    |
|city            |string    |null:false                    |
|home_number     |string    |null:false                    |
|building_name   |string    |                              |
|phone_number    |string    |null:false                    |
|order           |references|null: false, foreign_key: true|


### Association
・belongs_to :order

### orderテーブル

|Column          |Type      |Options                          |
|item            |references|nulnull: false, foreign_key: true|
|user            |references|nulnull: false, foreign_key: true|


### Association
・has_one :item
・has_one :user
