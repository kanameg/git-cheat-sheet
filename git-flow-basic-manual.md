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
remote:      https://github.com/kanameg/how-to-use/pull/new/feature/[feature-name]
remote: 
To https://github.com/kanameg/how-to-use.git
 * [new branch]      feature/[feature-name] -> feature/[feature-name]
Already on 'feature/[feature-name]'
Your branch is up to date with 'origin/feature/[feature-name]'.

Summary of actions:
- A new remote branch 'feature/[feature-name]' was created
- The local branch 'feature/[feature-name]' was configured to track the remote branch
- You are now on branch 'feature/[feature-name]'

$ 
```
