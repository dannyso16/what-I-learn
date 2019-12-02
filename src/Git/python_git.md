# python + git

subprocessを使う→コマンドを使える！→当然Gitもできる

```python
import subprocess
 
cmd = "git status"
```

[subprocess doc]( https://docs.python.org/ja/3/library/subprocess.html )

## call

```python
run_cmd = subprocess.call(cmd.split())
print(run_cmd) # return 0
```

実行の際はスペース区切りで渡す

もし`python child.py`のように実行すると，callはchildの実行が終わるまで待機する

返り血は終了時のコード０とか



## check_out

```python
run_cmd = subprocess.check_out(cmd.split())
print(run_cmd) # byte 文字列
```

byte文字列→b'hello\n world\r\n' みたいなん

コマンドラインで表示される文字列が返ってくる

strにするには `byte_str.decode("utf-8")`



## Popen

もし`python child.py`のように実行すると，Popenオブジェクトがかえって来る．これは新しいプロセス(child)を生成している．



