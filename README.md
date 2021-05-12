## usersテーブル

|Column             |Type     |Options               |
|nikname            |string   |null:false,unique:true|
|email              |string   |null:false,unique:true|
|encrypted_password |string   |null:false            |
|family_name        |string   |null:false            |
|first_name         |string   |null:false            |
|family_name_kana   |string   |null:false            |
|first_name_kana    |string   |null:false            |
|birthdate          |date     |null:false            |

### Association
・has_many :items, dependent: :destroy, foreign_key: :items
・has_one :address, dependent: :destroy
・has_many :order, dependent: :destroy

## itemsテーブル

|Column       |Type      |Options                     |
|name         |string    |null:false                  |
|text         |text      |null:false                  |
|category_id  |references|null:false,foreigen_key:true|
|condition_id |integer   |null:false                  |
|postage_id   |integer   |null:false                  |
|prefecture_id|integer   |null:false                  |
|prepare_id   |integer   |null:false                  |
|price        |references|null:false                  |
|user         |references|foreign_key:true            |


### Association
・belongs_to :user


### addressesテーブル

|Column          |Type      |Options                       |
|post_code       |integer   |null:false                    |
|prefecture_id   |integer   |null:false                    |
|city            |string    |null:false                    |
|home_number     |string    |null:false                    |
|building_name   |string    |                              |
|phone_number    |string    |unique: true                  |
|user            |references|null: false, foreign_key: true|


### Association
・belongs_to :user

### orderテーブル

|Column          |Type      |Options                          |
|item            |references|nulnull: false, foreign_key: true|
|user            |references|nulnull: false, foreign_key: true|

### Association
・has_one :item
・has_one :user
