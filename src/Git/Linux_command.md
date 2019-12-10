# Linux commands



## ファイル操作

### 空のファイルを作る

`touch XXX.txt`

### ファイルのコピー

`cp コピーするファイル名 コピー先のファイル名`

例えば，`cp test.txt test_copy.txt`

### 名前の変更

`mv 変更したいファイル 変更後の名前`

例えば，`mv test.txt renamed.txt`

### 閲覧

`cat ファイル名`

### ファイルの削除

`rm ファイル名`

### エクスプローラで開く

`start .` ：今のディレクトリを開く



## システム

### シャットダウン関係(Linux)

`shutdown 時間`

例えば，`shutdown now`：電源は切らない

`shutdown -h +1` ：1分後にシステム停止し，電源を切る

`shutdown -r now`：再起動

`shutdown -c`：予定されたシャットダウンをキャンセル

### ※Windwosの場合

`shutdown -[option]`で時間はなくてもいい

| オプション            | 説明                                                         |
| --------------------- | ------------------------------------------------------------ |
| -i                    | GUIインターフェイスを表示する                                |
| -l                    | ログオフを実行する（-mと併用不可）                           |
| -s                    | シャットダウンする                                           |
| -r                    | コンピュータを再起動する                                     |
| -a                    | シャットダウンを中止する                                     |
| -m *\\Compurter Name* | リモート作業時のコンピュータ名を指定する                     |
| -t *sec*              | シャットダウンまでの時間を指定する                           |
| -c *"Comment"*        | シャットダウン時のメッセージ（コメント）を指定する（最大127文字） |
| -f                    | アプリケーションを強制終了する                               |
| -d (u\|p):xx(:yy)     | シャットダウンの理由コードを指定する（下記参照）             |

[すべてのオプション](https://www.k-tanaka.net/cmd/shutdown.php)

![shutdown_gui](C:\Users\HOME\Documents\GitHub\what-I-learn\src\Git\Linux_command.assets\shutdown_gui-1575942615102.PNG)

x