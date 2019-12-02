# Git メモ



## git status等で日本語ファイル名が”\xxx\xxx”と数字の羅列になる

git statusコマンド等で日本語ファイル名が化ける場合はGitBash上から以下のコマンドを実行します。

```
$ git config --global core.quotepath false
```

これで日本語ファイル名も化けずに確認できる様になります。

git diff などは普通に日本語だったのでびびった（2019/11/17）



### cmdからファイルを所定のプログラムで開きたい

`start file_name` で開ける

macだと`open`みたい