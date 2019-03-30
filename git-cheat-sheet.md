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
*~         # 末尾に~が付くemacsのバックアップファイルは無視
*.swp      # vimのswapファイルも無視
.DS_Store  # macのプレビューファイル
```


## 通常運用で使用するコマンド

### 通常の更新手順
通常は以下のような手順でファイルを更新しリモートレポジトリの更新を行う。

1. リモートレポジトリからローカルに複製 `(clone)`
1. ファイルの編集
1. 差分を見て変更の確認 `(diff)`
1. ローカルレポジトリの状態を確認 `(status)`
1. 変更や追加したファイルのステージング `(add)`
1. ステージングした内容をローカルレポジトリにコミット`(commit)`
1. 変更の確認 `(log)`
1. リモートレポジトリにローカルの内容をプッシュ `(push)`

以下に各手順を詳細に説明する。


--------------------------------------------------------------------------------------------------


### 複製作成 (clone)
リモートリポジトリからローカルにリポジトリを複製
```
$ git clone [remote repository URL]
```

### 差分表示 (diff)

![リポジトリの内部構造](rep-internal.png "リポジトリの内部構造")

ローカルリポジトリのワークツリー(work tree)に加えた変更とインデックス(index)の差分を表示する。
```
$ git diff
```

ローカルリポジトリのワークツリーと現在のコミットの先頭(HEAD)を比較し差分を表示する。
```
$ git diff HEAD
```

インデックスとコミット先頭(HEAD)を比較し差分を表示する。ワークツリーに変更を加えている状態で次のコミットでコミットされる変更内容を確認したい場合に使用する。
```
$ git diff --cached
```

### 状態表示 (status)
現在のローカルリポジトリの状態取得する。
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

ファイル名を指定してステージングを行う。
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

### ステージングのリセット (reset)
間違ってインデックスにステージングしてしまった場合に、`reset`コマンドを使うことによってステージングをキャンセルできる。
ファイルを直接指定してステージング済のファイルを解除する。
```
$ git reset [file]
```


### 履歴の表示 (log)
リポジトリへの変更履歴を表示する。
```
$ git log
```
