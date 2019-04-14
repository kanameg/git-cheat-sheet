# 競合（コンフリクト）の解決

マージを行った際に編集箇所が競合した場合、gitのマージ処理では自動で解決できないため手動で編集を行い解決する必要があります。競合（コンフリクト）が発生すると以下のような結果が出力されます。

* 競合（コンフリクト）が発生した場合
```
$ git pull
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 2 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://[remote-repository-url]
   3df5b95..02972e2  develop    -> origin/develop
Auto-merging test.md
CONFLICT (content): Merge conflict in test.md
Automatic merge failed; fix conflicts and then commit the result.
$ 
```

この場合、`test.md`で競合が発生し自動解決できなかったため`Automatic merge failed; fix conflicts and then commit the result.`という結果が出力されています。

競合が発生したファイルをエディタで開くと以下のような内容になって競合箇所を示しています。

* 競合（コンフリクト）の内容
```
<<<<<<< HEAD
Aさんが内容を変更(変更の元内容)
=======
Bさんが内容を変更(変更の元内容)
>>>>>>> 02972e205223ab302da7092800b91037d79941f2
```

`<<<<<<< HEAD`から`>>>>>>> 02972e205223ab302da7092800b91037d79941f2`までが競合（コンフリクト）箇所のため、内容を確認しながら不要部分を削除して編集を行います。

* 編集して競合（コンフリクト）を解決
```
Aさんが内容を変更(変更の元内容)
```

