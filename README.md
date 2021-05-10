## usersテーブル

|Column          |Type     |Options               |
|nikname         |string   |null:false,unique:true|
|email           |string   |null:false,unique:true|
|password        |string   |null:false            |
|family_name     |string   |null:false            |
|first_name      |string   |null:false            |
|family_name_kana|string   |null:false            |
|first_name_kana |string   |null:false            |
|birthdate       |date     |null:false            |

### Association
・has_many :items, dependent: :destroy, foreign_key: :items
・has_one :address, dependent: :destroy
・has_many :card, dependent: :destroy

## itemsテーブル

|Column       |Type      |Options                     |
|name         |string    |null:false                  |
|text         |text      |null:false                  |
|category     |references|null:false,foreigen_key:true|
|brand        |string    |                            |
|condition    |integer   |null:false                  |
|postage      |integer   |null:false                  |
|prefecture   |integer   |null:false                  |
|prepare      |integer   |null:false                  |
|price        |references|null:false                  |
|seller       |references|null:false,foreign_key:true |
|buyer        |references|foreign_key:true            |


### Association
・belongs_to :user


### addressesテーブル

|Column          |Type      |Options                       |
|family_name     |string    |null:false                    |
|first_name      |string    |null:false                    |
|family_name_kana|string    |null:false                    |
|first_name_kana |string    |null:false                    |
|post_code       |integer   |null:false                    |
|prefecture_id   |integer   |null:false                    |
|city            |string    |null:false                    |
|home_number     |string    |null:false                    |
|building_name   |string    |                              |
|phone_number    |string    |unique: true                  |
|user_id         |references|null: false, foreign_key: true|


### Association
・belongs_to :user

## cardsテーブル

|Column         |Type      |Options                       |
|payjp_id       |string    |null: false, unique: true     |
|customer_id    |string    |null: false                   |
|credit_number  |integer   |null:false                    |
|expiration_year|integer   |null:false                    |
|security_number|integer   |null:false                    |
|user           |references|null: false, foreign_key: true|




### Association
・belongs_to :user
