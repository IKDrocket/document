# ステージングエリアにあげる

```
git add .
```

# commit する

```
git commit -m "commit message!!"
```

# remote リポジトリに push する

```
git push
git push origin main
```

# ブランチを切る

```
git branch

git branch develop
git checkout develop

git checkout -b develop
```

# ブランチをマージする

```
git checkout main
git merge develop

# ブランチを削除
git branch -d develop
```

# リモートリポジトリから強制 pull する

```
# リモートの最新を取得
git fetch origin master

# ローカルのmasterを、リモート追跡のmasterに強制的に合わせる
git reset --hard origin/master
```

# コミットはせずに変更を退避
```
# 変更を退避
git stash -u

# 退避した作業の一覧を確認
git stash list
stash@{0}: WIP on test: xxxx
stash@{1}: WIP on commit-sample: xxxx

# 退避した作業を戻す
git stash apply stash@{0}
```


# コミット前に戻す

```
// 直前のコミット操作を取り消す
git reset --soft HEAD^

// 直前のコミット作成の直後に戻す
git reset --hard HEAD^
```

# マージ前に戻す

```
// マージしたらコンフリクトした。やっぱりやめる。
git reset --soft HEAD^

// マージしたらコンフリクトした。その後編集したが、やめる。
git reset --hard HEAD
```
