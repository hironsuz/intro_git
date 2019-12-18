# Githubの初期設定

## ユーザ名の登録
```bash
git config --global user.name "hironsuz"
```
## メールアドレスの登録
```bash
git config --global user.email hironsuz@gmail.com
```

# 新規プロジェクトの開始
デスクトップにintro_gitという名前でディレクトリを作成する。
```bash
cd desktop
mkdir intro_git
```
intro_gitディレクトに移動する。
```bash
cd ~/desktop/intro_git/
```
その中にfirst.txtというファイルを作成する。
```bash
vi first.txt
```
初期化する
```bash
git init
```
すると、.gitディレクトリに、Gitリポジトリが作られる。
```bash
Reinitialized existing Git repository in /Users/hironsuz/Desktop/intro_git/.git/
```

.gitディレクトリの中身を確認してみる。
```bash
ls -a .git
```
```bash
.              HEAD           hooks          logs
..             config         index          objects
COMMIT_EDITMSG description    info           refs
```

# 基本的なワークフロー
① ファイルの変更をステージングエリアへ追加する(git add)<br>
② ローカルリポジトリにコミットする(git commit)<br>
③ リモートリポジトリにプッシュする(git push)<br>

intro_gitディレクトリへ移動する
```bash
cd ~desktop/intro_git
```

first.txtに変更を加える。
```bash
vi first.txt
# なんかを変更
```

変更をステージングエリアへ追加する。
```bash
git add first.txt
```
次にコミットする
```bash
git commit
```

するとメッセージ入力画面がvimで開かれるので、
ここでは"initial commit"と入力する。

```
  1 initial commit # <- メッセージ入力箇所
  2 # Please enter the commit message for your changes. Lines starting
  3 # with '#' will be ignored, and an empty message aborts the commit.
  4 #
  5 # On branch master
  6 # Your branch is up to date with 'origin/master'.
  7 #
  8 # Changes to be committed:
  9 #       modified:   first.txt
 10 #
 ```

githubへプッシュする。
プッシュするリポジトリをGithubで作成する。
Githubを開き、"new repository"からintro_gitという名前でリポジトリを作成する。
Githubに、intro_git.gitを登録する。

```bash
git remote add origin https://github/hironsuz/intro_git.git
```

リモートリポジトリにプッシュする。
```bash
git push -u origin master
```

# 変更をコミットする
ファイルを変更したら、、
① ステージングエリアへ追加
② リポジトリにメッセージをつけてコミット

ステージングエリアは、コミットするファイルを選択するためのエリア。

ステージングエリアへの追加
```bash
git add [ファイル名]
git add . # すべてのファイル
```

メッセージをつけてコミットする。ひとつの変更ごとにコミットする。
```bash
git commit
```

実際にやってみる。
first.txtを開いて変更を加える。
```bash
vi first.txt
```

状態を確認する。
```bash
git status
```
first.txtが変更されたと表示される。
```bash
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   first.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

first.txtをステージングエリアへ移動する。
```bash
git add .
```
状態を確認する。
```bash
git status
```
ファイル名が緑色になりステージングエリアへ移動したことを確認できた。
```bash
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   first.txt
```

コミットする。


```bash
git commit -v # -vをつけることで変更箇所が表示される
```

```bash
  1 add, commitのコマンドを追記
  2
  3 講座を受講したから
  4 # Please enter the commit message for your changes. Lines starting
  5 # with '#' will be ignored, and an empty message aborts the commit.
  6 #
  7 # On branch master
  8 # Your branch is up to date with 'origin/master'.
  9 #
 10 # Changes to be committed:
 11 #       modified:   first.txt
 12 #
 13 # ------------------------ >8 ------------------------
 14 # Do not modify or remove the line above.
 15 # Everything below it will be ignored.
 16 diff --git a/first.txt b/first.txt
 17 index 87e0a8f..45c7e56 100644
 18 --- a/first.txt
 19 +++ b/first.txt
 20 @@ -1,2 +1,4 @@
 21  gitの練習をしていきます。
 22  基本的なワークフローを学びます。
 23 +・git add
 24 +・git commit
 ```

コミットを確認する。
```bash
git log
```
変更履歴が表示される。
```bash
~/d/intro_git ❯❯❯ git log
commit ca67a3ccc164c663271f6497a278ecc2df0c0320 (HEAD -> master)
Author: hironsuz <hironsuz@gmail.com>
Date:   Wed Dec 18 13:54:18 2019 +0900

    add, commitのコマンドを追記

    講座を受講したから

commit 8b278d5f7dfdd8d4b164f28cdc5d043b69cb0a7e (origin/master)
Author: hironsuz <hironsuz@gmail.com>
Date:   Wed Dec 18 13:22:13 2019 +0900

    initial commit
,,,,,,

```
