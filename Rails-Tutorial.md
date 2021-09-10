### railsアプリを作成する
```
$ rails _6.0.3_ new toy_app
$ cd toy_app/
```
### Gemfileを変更時に実行する
```
$ bundle install --without production
```

Q. bundle install時のエラー
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
A. Gemfaile.lockを削除して再度実行する

### StaticPagesコントローラを生成する
```
$ rails generate controller StaticPages home help
```
### StaticPagesコントローラを削除する（ファイル単体を削除しても不十分）
```
$ rails destroy  controller StaticPages home help
```


### railsでモデルをscaffoldを使って作成する
```
$ rails generate scaffold User name:string email:string
```

### railsでモデルを作成する
```
$ rails generate model User name:string email:string
```
### railsでモデルを削除する
```
$ rails destroy model User
```

### データベースをマイグレートする
```
$ rails db:migrate
```

### データベースを`db:rollback`で1つ前の状態に戻す
```
$ rails db:rollback
```

### データベースを最初の状態に戻す
```
$ rails db:migrate VERSION=0
```

### railsコンソールを使用する
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

### rubocopを導入する
```
$ gem install rubocop-rails rubocop-rspec rubocop-performance rubocop
```


### 省略コマンド一覧
| 完全なコマンド | 短縮形 |
|--|--|
| $ rails console | $ rails c |
| $ rails generate | $ rails g |
| $ rails test | $ rails t |
| $ bundle install | $ bundle |
