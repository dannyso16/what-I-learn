# Git メモ



## git status等で日本語ファイル名が”\xxx\xxx”と数字の羅列になる

git statusコマンド等で日本語ファイル名が化ける場合はGitBash上から以下のコマンドを実行します。

```
$ git config --global core.quotepath false
```

これで日本語ファイル名も化けずに確認できる様になります。

git diff などは普通に日本語だったのでびびった（2019/11/17）



## cmdからファイルを所定のプログラムで開きたい

`start file_name` で開ける

macだと`open`みたい



## localに新しいブランチを作って，GitHubから特定のブランチをpullする

`git pull origin pullしたいリモートブランチ名:ローカルブランチ名`

例えば，`git pull origin enhanceA:enhanceA`



## いらないブランチを消す

`git branch -d branch_name`



### git log

- `--oneline`：一行で
- `--graph`：ソースツリーみたい



## 逆マージ

```
git checkout enhance
git merge develop
```

**コミットが済んでいないファイルが残っている状態で git merge しない**

コミットが済んでいない状態で git merge を行うと、ブランチの変更の取り込み漏れの原因になります。全てコミットが済んでいる状態で git merge するようにしましょう。

## マージを元に戻す方法

ここでは、マージを元に戻す方法をご紹介します。

上記のように、git merge により衝突が発生しても、修正方法はありますが、マージ自体を元に戻したい場合もあります。その場合、マージ後にコミットしたか、していないかによりコマンドが異なります。

マージした後、未だコミットしていない場合

```
git reset --hard HEAD
```

マージした後、コミットも行っている場合

```
git reset --hard ORIG_HEAD
```



## コミットメッセージを書き換えたい！！

#### 直前のコミットの場合

```
git commit -m "〇を変更う"
git commit --amend -m "〇を変更"
```

[Gitのコミットメッセージを後から変更する方法をわかりやすく書いてみた](https://www.granfairs.com/blog/staff/git-commit-fix)

二つ以上の前でも変更できるようだ



## HEADに戻りたい

```
git reset --hard HEAD
```

※もちろんUntrackedは対象外。Untrackedを消したい場合は、コメントで教えてもらった「git clean -f」を使う。もしくは、「git add .」して一旦管理下に入れて上記を行う。



### ファイル単位で戻したい

`reset --hard`はファイル単位ではできないので…

#### 対象がadd済みファイル(インデックス&ワーキングツリーに存在)

まずインデックスを戻して、次にワーキングツリーを戻す。

```
git reset HEAD <file>
git checkout <file>
```

#### 対象が未addファイル(ワーキングツリーのみに存在)

ワーキングツリーを戻す。

```
git checkout <file>
```



## ブランチを消したい

### リモートブランチ

```
git push --delete origin branch_name
```

### ゾンビ化したとき

リモートリポジトリを直接消すと参照は残って消せなくなる

```
git push --delete origin branch_name
error: unable to delete 'branch_name': remote ref does not exist
error: failed to push some refs to 'https://github.com/dannyso16/hogehoge.git'
```

pruneで刈り取る

```
git remote prune origin
```



## Git push の取り消し

### 過ちを隠す（commitを取り消して，リモートから消す）

#### ローカルも書き換えるとき

```c
// 直前のコミットなら… ひとつ前に戻す
git reset --hard HEAD^

// 強制的にpush
git push -f origin (remote branch 名)
```

#### ローカルはそのままにしたい（未確認）

```c
// リモートの参照を強制的に戻す
git push -f origin {sha-1 like 8dj2dga...}:{remote branch name}
```



### 過ちを認める（間違いコミットを打ち消すrevertコミットを作って追加でpush）

安全だけどログが汚くなる

```ba
// 直前のコミットを打ち消すコミット
git revert HEAD
// 最新に加えて，さらに過去３つのコミットを打ち消す
git revert HEAD~3

// 新しいコミットなのでconflictしないし，-fで強制しなくていい
git push origin {branch name}
```

