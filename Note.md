# Section 3
## 22. 現在の変更状況を確認しよう

```shell
# 変更状況を確認する時
~ $ git status
```


## 23. 何を変更したのかを確認しよう
` git diff ` を使うことでstage--worktree間、stage--repository間の差分を確認することができる
```shell
# stageとworktreeの差分を見る時
~ $ git diff

# stageとrepositoryの差分を見る時
~ $ git diff --staged
```

## 24. 変更履歴を確認しよう
` git log ` コマンドで変更履歴を確認することができる。

```shell
# 一行で表示する
~ $ git log --oneline

# ファイルの変更差分を表示する
~ $ git log -p Note.md

# 表示するコミット数を制限する
~ $ git log -n <num of commits>
```

<div style="page-break-before:always"></div>

## 25. ファイルの削除を記録しよう
` git rm `を用いることでリポジトリからファイルを削除することができる。

 ```shell
# ファイルごと削除
~ $ git rm <ファイル名>
~ $ git rm -r<ディレクトリ名>

# ファイルを残したい時 (リポジトリからは消したい , i. e. Passwordを載せたファイルなど)
~ $ git rm --cached <ファイル名>
 ```

## 26. ファイルの移動を記録する
`git mv`を使うことでファイルの移動を記録できるが、通常のコマンドを用いても大体できるので、無理に使う必要はない。
` git mv `を使うと単純にファイル名を変更することができる。
```shell
~ $ git mv <old file> <new file> 

# 以下のコマンドと同じ
~ $ mv <old file> <new file>
~ $ git rm <old file>
~ $ git add <new file>

```


## 27. GitHubにpushしよう
GitHubなどのリモートリポジトリに変更をアップする

1. リモートリポジトリを追加する
```shell
~ $ git remote add origin <url>
# "origin"という名のショートカット でurlのリモートリポジトリを登録する
``` 
originという名前でリモートリポジトリと通信できる。
clone元だからoriginという名前をつける。

2. リモートリポジトリへと送信する
``` shell
~ $ git push <Remote name> <Branch name> 
~ $ git push origin master
```
`-u` をつけると次回以降にorigin master を省略できる

## 28. Githubの見方
### ファイルの閲覧について
- Raw  
  生データ、コピペするのに便利
- Blame  
  変更の責任者を確認することができる
- History
  コミットの履歴を見るとこができる

## 29. コマンドにエイリアスをつけよう

### gitの設定を変更する
`git config`コマンドをつかう。  
`--global`をつけることでPC全体の設定となる

```shell
# エイリアスをつけることで入力が楽になる
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.co checkout
```

## 30. gitで管理したくないファイルを無視しよう
バージョン管理したくないファイル
- Password
- 自動生成されるファイル
- 重すぎるファイル

.gitignore を作成して無視するファイルを記述する
```shell
# 指定したファイルを除外
index.html
# ルートディレクトリを指定
/root.html
# ディレクトリ以下を除外
dir/
# /以外の文字列にマッチ「*」
```

# Section 4: 変更を元に戻そう
## 31. ファイルへの変更を取り消そう

ファイルへの変更を取り消すときは　`git checkout`コマンドを使用する

```shell
~ $ git checkout -- <file name>
~ $ git checkout -- <directory name>

# 全変更を取り消す
~ $ git checkout --.
```

` checkout `コマンドはブランチの変更にも用いるため、 ファイルとブランチの区別をつけるために` -- `をつける。


## 32. ステージした変更を取り消そう
` git reset ` を用いることでステージを取り消すことができる。
指定した変更をステージから取り消すだけなので、ワークツリーのファイル自体には影響を与えない。
```shell
~ $ git reset HEAD <file name>
~ $ git reset HEAD <directory name>

# 全変更を取り消す場合
~ $ git reset HEAD .
```


## 33. 直前のコミットをやり直そう
直前のコミットを修正した時は ` git commit --amend `コマンドを用いる。  
リモートリポジトリにPushしたら、git のコミット履歴がおかしくなってしまうため、行ってはいけない。
```shell
# ローカルリポジトリにコミットした内容を修正することができる
~ $ git commit --amend
```

<div style="page-break-before:always"></div>

# Section 5. GitHubとやりとりをしよう
## 34. リモートの情報を確認しよう
` git remote `コマンドを用いることで設定しているリモートリポジトリの情報を確認することができる。

```shell
~ $ git remote

# 対応するurl を確認する時は　'-v' をつける
~ $ git remote -v
    origin	https://github.com/takaaki-qgis/git_tutorial.git (fetch)
    origin	https://github.com/takaaki-qgis/git_tutorial.git (push)

```

## 35. リモートリポジトリを追加しよう
リモートリポジトリは複数登録することができる
- バックアップ用のリポジトリを作りたい時
- プロジェクトが複数のチームに跨ぐ時
```shell
~ $ git remote add <remote name> <remote URL>
```

## 36.リモートから情報を取得しよう (fetch)
リモートからの情報を取得するのには ` git fetch `と` git pull `の二つのコマンドがある。
```shell
~ $ git fetch <remote name>
# fetchとは「取ってくる」という意味
```

# Section 6. branch と mergeを使いこなそう

[^1]: fetchとは「取ってくる」という意味


# Section 7. GitHubを利用した開発手順の流れ