# ステージングエリアにあげる

```
$ git add .
```

# commit する

```
$ git commit -m "commit message!!"
```

# remote リポジトリに push する

```
$ git push origin main
```

# ブランチを切る

```
$ git branch

$ git branch develop
$ git checkout develop

$ git checkout -b develop
```

# ブランチをマージする

```
$ git checkout main
$ git merge develop
$ git branch -d develop
```

# リモートリポジトリから強制 pull する

```
// 1) リモートの最新を取ってきておいて・・
$ git fetch origin master

// 2) ローカルのmasterを、リモート追跡のmasterに強制的に合わせる！
$ git reset --hard origin/master
```

# コミット前に戻す

```
// 直前のコミット操作を取り消す
git reset --soft HEAD^

// 直前のコミット作成の直後に戻す
git reset --hard HEAD^
```
