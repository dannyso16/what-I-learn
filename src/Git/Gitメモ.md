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



## 逆マージ

```
git checkout enhance
git merge develop
```

### コミットが済んでいないファイルが残っている状態で git merge しない

コミットが済んでいない状態で git merge を行うと、ブランチの変更の取り込み漏れの原因になります。全てコミットが済んでいる状態で git merge するようにしましょう。

### マージを元に戻す方法

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