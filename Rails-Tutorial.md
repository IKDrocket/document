### rails アプリを作成する

```
$ rails _6.0.3_ new toy_app
$ cd toy_app/
```

### Gemfile を変更時に実行する

```
$ bundle install --without production
```

Q. bundle install 時のエラー

```
$ bundle install --without production
The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java`.
Fetching gem metadata from https://rubygems.org/............
Fetching gem metadata from https://rubygems.org/.
You have requested:
  listen = 3.1.5

The bundle currently has listen locked at 3.7.0.
Try running `bundle update listen`

If you are updating multiple gems in your Gemfile at once,
try passing them all to `bundle update`
```

A. Gemfaile.lock を削除して再度実行する

### StaticPages コントローラを生成する

```
$ rails generate controller StaticPages home help
```

### StaticPages コントローラを削除する（ファイル単体を削除しても不十分）

```
$ rails destroy  controller StaticPages home help
```

### rails でモデルを scaffold を使って作成する

```
$ rails generate scaffold User name:string email:string
```

### rails でモデルを作成する

```
$ rails generate model User name:string email:string
```

### rails でモデルを削除する

```
$ rails destroy model User
```

### データベースをマイグレートする

```
$ rails db:migrate
```

### データベースを`db:rollback`で 1 つ前の状態に戻す

```
$ rails db:rollback
```

### データベースを最初の状態に戻す

```
$ rails db:migrate VERSION=0
```

### rails コンソールを使用する

```
$ rails console
irb(main):001:0> first_user = User.find_by(id: 3) # User.first
   (0.3ms)  SELECT sqlite_version(*)
  User Load (0.2ms)  SELECT "users".* FROM "users" WHERE "users"."id" = ? LIMIT ?  [["id", 3], ["LIMIT", 1]]
=> #<User id: 3, name: "testname", email: "test@examlpe.com", created_at: "2021-08-29 08:41:08", updated_at: "2021-08-29 08:41:08">

irb(main):002:0> first_user.microposts
  Micropost Load (0.1ms)  SELECT "microposts".* FROM "microposts" WHERE "microposts"."user_id" = ? LIMIT ?  [["user_id", 3], ["LIMIT", 11]]
=> #<ActiveRecord::Associations::CollectionProxy [#<Micropost id: 5, content: "testtext", user_id: 3, created_at: "2021-08-29 16:05:30", updated_at: "2021-08-29 16:05:30">]>

irb(main):003:0> micropost = first_user.microposts.first
  Micropost Load (0.2ms)  SELECT "microposts".* FROM "microposts" WHERE "microposts"."user_id" = ? ORDER BY "microposts"."id" ASC LIMIT ?  [["user_id", 3], ["LIMIT", 1]]
=> #<Micropost id: 5, content: "testtext", user_id: 3, created_at: "2021-08-29 16:05:30", updated_at: "2021-08-29 16:05:30">

irb(main):004:0> micropost.user
=> #<User id: 3, name: "testname", email: "test@examlpe.com", created_at: "2021-08-29 08:41:08", updated_at: "2021-08-29 08:41:08">
```

```
$ rails console --sandbox
```

### rubocop を導入する

```
$ gem install rubocop-rails rubocop-rspec rubocop-performance rubocop
```

### 省略コマンド一覧

| 完全なコマンド   | 短縮形    |
| ---------------- | --------- |
| $ rails console  | $ rails c |
| $ rails generate | $ rails g |
| $ rails test     | $ rails t |
| $ bundle install | $ bundle  |

```
# 範囲オブジェクト0..16を使って、各要素の２乗を出力してください。
(0..16).each do  |num| puts num ** 2 end

# yeller（大声で叫ぶ）というメソッドを定義してください。
def yeller(array)
  array.map(&:downcase).join
end

# random_subdomainというメソッドを定義してください。
def random_subdomain()
  ('a'..'z').to_a.shuffle[0..7].join
end

def string_shuffle(s)
  s.split('').shuffle.join
end
```

# 統合テスト

```
# 作成
$ rails generate integration_test site_layout
# 実行
$ rails test:integration
```

## User オブジェクト作成

## create

```
>> User.new
=> #<User id: nil, name: nil, email: nil, created_at: nil, updated_at: nil>

>> user = User.new(name: "Michael Hartl", email: "michael@example.com")
=> #<User id: nil, name: "Michael Hartl", email: "michael@example.com",
created_at: nil, updated_at: nil>

>> user.save

>> user
=> #<User id: 1, name: "Michael Hartl", email: "michael@example.com",
created_at: "2019-08-22 01:51:03", updated_at: "2019-08-22 01:51:03">
```

```
>> User.create(name: "A Nother", email: "another@example.org")

>> User.find(1)
=> #<User id: 1, name: "Michael Hartl", email: "michael@example.com",
created_at: "2019-08-22 01:51:03", updated_at: "2019-08-22 01:51:03">

>> User.all
>> User.first
```

## update

```
>> user.update(name: "The Dude", email: "dude@abides.org")

>> user.update_attribute(:name, "El Duderino")
```
