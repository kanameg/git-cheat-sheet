# Gitチートシート

## ツール初期設定

ユーザ名を設定（全リポジトリ共通） (user.name)
```
$ git config --global user.name "[name]"
```

emailアドレスを設定（全リポジトリ共通） (user.email)
```
$ git config --global user.email "[email address]"
```


## 通常運用で使用するコマンド

### 複製作成 (clone)
リモートリポジトリからローカルにリポジトリを複製
```
$ git clone [remote repository URL]
```

### 差分表示 (diff)
ローカルリポジトリのワークツリー(work tree)に加えた変更とインデックス(index)の差分を表示する
```
$ git diff
```

ローカルリポジトリのワークツリーと現在のコミットの先頭(HEAD)を比較し差分を表示する
```
$ git diff HEAD
```


### 状態表示 (status)
現在のローカルリポジトリの状態取得
```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	git-cheat-sheet.md

nothing added to commit but untracked files present (use "git add" to track)
$ 
```
