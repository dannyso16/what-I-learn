# memo

## 3d plot as subplot

![../../_images/sphx_glr_subplot3d_001.png](.\mmo.assets\sphx_glr_subplot3d_001.png)

こういうのがしたい

```python
ax = fig.add_subplot(1, 2, 1, projection='3d')
```



## 一つの画像に複数のプロット

[ここ](http://ailaby.com/matplotlib_fig/)

```python
x = np.linspace(-3, 3, 20)
y1 = x
y2 = x ** 2
 
# figure は 1 つ
plt.figure(figsize=(3, 4))
 
plt.subplot(2,1,1)
plt.plot(x, y1)
 
plt.subplot(2,1,2)
plt.plot(x, y2)
 
plt.show()
```

![plot_win_1](.\mmo.assets\plot_win_1.png)



## ディレクトリ

### カレントディレクトリ

- カレントディレクトリを取得・確認: `os.getcwd()`
- カレントディレクトリを変更（移動）: `os.chdir()`

なお、実行しているスクリプトファイル（`.py`）のパスは`__file__`で取得できる

### ファイル操作は**shutil**が便利そう

[[Python] フォルダやファイルのコピー、移動、削除（shutilモジュール）](https://hibiki-press.tech/learn_prog/python/shutil_copy_move_rmtree/1305)

### ファイルの有無

```python
os.path.exists(path) # file も directory も

os.path.isfile(path)
os.path.isdir(path)
```





## オブジェクトの永続化 pickle

[pickle documents](https://docs.python.org/ja/3/library/pickle.html#module-pickle) 



### arrayの保存　np.save

```python
np.save(
    file, # データを保存するファイル名 joge.npy
    arr,  # 配列型オブジェクト（listやnp.array)
    fix_imports=True # Python2でも使えるようにするかどうか
)
```

### arrayの読み込み　np.load

```python
np.load(
    file="tset.npy",        # npyかnpz拡張子のファイルを指定
    allow_pickle=True,      # npy/npzで保存されたpickleファイルを読み込むかどうか (デフォルトではTrue)
    fix_imports=True,       # Python2との互換機能、Trueならpy2製ファイルを読み込める　（デフォルトではTrue）
    encoding="ASCII",       # Python2で作られた文字列を読み込むときの文字コード指定　（デフォルトではASCII）
)
```

