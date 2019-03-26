# Gitチートシート

## ツール初期設定

### ユーザ関連の設定 (user)
ユーザ名を設定（全リポジトリ共通） (user.name)
```
$ git config --global user.name "[name]"
```

emailアドレスを設定（全リポジトリ共通） (user.email)
```
$ git config --global user.email "[email address]"
```

### トラッキングの制限 (.gitigunore)
`.gitignore`ファイルを作成して、トラッキングしないファイル名のパターンをテキストで記述しておく

```
*~      # 末尾に~が付くemacsのバックアップファイルは無視
*.swp   # vimのswapファイルも無視
```


## 通常運用で使用するコマンド

### 複製作成 (clone)
リモートリポジトリからローカルにリポジトリを複製
```
$ git clone [remote repository URL]
```

### 差分表示 (diff)

![図1. リポジトリ内の構造](rep-internal.png)

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

### 変更ファイルのステージング (add)
ステージングとは、ワークツリーにのファイルに加えた変更、新規のファイル追加、トラッキング中のファイルを削除した場合に、その変更をインデックスに反映すること。

ファイル名を指定してステージングを行う
```
$ git add [file]
```

トラッキング中の全てのファイルに加えた変更をステージングする。新規のファイルやファイルを削除した場合はステージングされない。
```
$ git add -u
```

全てのファイルをステージング行う。ゴミファイルなどもステージングされる可能性があるので注意。`.gitignore`ファイルでトラッキングしたくないファイルは指定しておいたほうが良い。
```
$ git add -A
```


### 履歴の表示 (log)
リポジトリへの変更履歴を表示する。
```
$ git log
```
