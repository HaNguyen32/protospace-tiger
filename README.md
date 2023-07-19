# 実装したい機能

## ユーザー管理機能
#### 必要な項目
- メールアドレス
- パスワード
- パスワード再入力
- 名前
- プロフィール
- 所属
- 役職
新規登録ボタン

## 投稿機能
#### 必要な項目
- プロトタイプの名称
- キャッチコピー
- コンセプト
- プロトタイプの画像
保存するボタン

# テーブル設計
- コメント
送信するボタン
## users
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| email              | string     | null: false, unique: true      |
| password           | string     | null: false                    |
| encrypted_password | string     | null: false                    |
| name               | string     | null: false                    |
| profile            | string     | null: false                    |
| Affiliation        | string     | null: false                    |
| occupation         | string     | null: false                    |

### Association
- has_many :prototypes
- has_many :comments

## prototypes
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| title              | string     | null: false                    |
| catch_copy         | text       | null: false                    |
| concept            | text       | null: false                    |
| user_id            | references | null: false, foreign_key: true |

### Association
- has_many :comments
- belongs_to :user

## comments
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| comment            | text       | null: false                    |
| user_id            | references | null: false, foreign_key: true |
| prototypes_id      | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :prototype
