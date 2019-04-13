# git flow 簡易マニュアル
![](git-flow-logo.png)

## リポジトリの取得とgit flowの開始

リモートからリポジトリを取得してgit flowを利用できるように設定します。
```
$ git clone [repository-URL]

$ git flow init -d
```


## featureブランチの開始

追加機能を開発するために、新たなブランチを開始します。このコマンドにより`develop`ブランチから`feature/[feature-name]`ブランチが作成され、`feature/[feature-name]`ブランチに切り替わります。

```
$ git flow feature start [feature-name]
Switched to a new branch 'feature/[feature-name]'

Summary of actions:
- A new branch 'feature/[feature-name]' was created, based on 'develop'
- You are now on branch 'feature/[feature-name]'

Now, start committing on your feature. When done, use:

     git flow feature finish [feature-name]

$ 
```

ブランチ作成後は、他人と共用できるようにリモートへプッシュしておくと便利です。※初回だけでOK

```
$ git flow feature publish [feature-name]
Total 0 (delta 0), reused 0 (delta 0)
remote: 
remote: Create a pull request for 'feature/[feature-name]' on GitHub by visiting:
remote:      https://[remote-repository-url]/pull/new/feature/[feature-name]
remote: 
To https://[remote-repository-url]
 * [new branch]      feature/[feature-name] -> feature/[feature-name]
Already on 'feature/[feature-name]'
Your branch is up to date with 'origin/feature/[feature-name]'.

Summary of actions:
- A new remote branch 'feature/[feature-name]' was created
- The local branch 'feature/[feature-name]' was configured to track the remote branch
- You are now on branch 'feature/[feature-name]'

$ 
```

## featureブランチの終了
機能を追加してながらコミットを行っていき、機能の作成が完了するとブランチでの作業を終了して`develop`ブランチにマージします。

コミットを完了した状態で以下のコマンドを実行して`develop`ブランチにマージを実行します。
```
$ git flow feature finish -k [feature-name]
```

`develop`ブランチが成長済だとコンフリクトが発生する場合があるので、その場合はコンフリクトの発生したファイルをエディタで解決し、再度コマンドを実行します。

コマンドが完了して正しくマージが完了していれば、自動的に`develop`ブランチに切り替わるので、プッシュを行いリモートに適用します。
```
$ git push
```

## 共同作業者がfeatureブランチで作業
プッシュしたリモートのブランチを使って、共同作業者が編集作業を行うことも可能です。
その場合は、クローンを実行後git-flowを設定し、`feature/[feature-name]`を取り出して作業を開始します。
```
$ git clone [repository-URL]
$ git flow init -d

$ git branch
* develop  ← feature/[function-name]がない!
  master
  
$ git flow feature track [function-name]
Branch 'feature/[function-name]' set up to track remote branch 'feature/[function-name]' from 'origin'.
Switched to a new branch 'feature/[function-name]'

Summary of actions:
- A new remote tracking branch 'feature/[function-name]' was created
- You are now on branch 'feature/[function-name]'

$ git branch
  develop
* feature/[function-name]  ← feature/[function-name]が持ってこられた!
  master
```

共同作業者によりリモートが修正されている場合は、プルを行いローカルを最新化することができます。

```
$ git flow feature pull origin
Pulled origin's changes into feature/[function-name].
$ 
```
