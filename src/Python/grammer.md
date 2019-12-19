# Python Grammer



## assert

> 条件式がTrueではない時に、例外を投げます。
> これを仕込んでおくと、それまでちゃんと動いていたコードが、いじっているうちにいつの間にか想定と異なる振る舞いをするようになった時に、いち早く気づくことが出来ます。「とにかく想定と違ったら止める」というだけで良いなら、unittest等のテストクラスを書かなくていいので便利です。



### 構文

`assert 条件, Faseの時のString`

この時 Assertion Errorを投げるので

```python
try:
    kitai = 100
    assert kitai==100, "期待する値と違うで"
except AssertionError as err:
    print("AssertionError: ", err)
```

### 無効化

実行時に `python hoge.py -o`するのみ

`__debug__` が trueの場合（デフォルト）でasset できる．しかし，`__debug__`は再代入不可能なので，実行時にオプションをつけよう

### raw文字列

エスケープシーケンスを無視できる

```python
rs = r'a\tb\nA\tB'
print(rs)
# a\tb\nA\tB

print(type(rs))
# <class 'str'> ただのString

print(rs == 'a\\tb\\nA\\tB')
# True
```

パスを書くときに便利だが，**末尾が奇数個のバックスラッシュで終わる文字列はエラー**になるので注意。この場合は通常の文字列で書くか、末尾だけ通常文字列で書いて連結する必要がある。

```python
path2 = 'C:\\Windows\\system32\\'
# rpath2 = r'C:\Windows\system32\'
# SyntaxError: EOL while scanning string literal
rpath2 = r'C:\Windows\system32' + '\\'
print(path2 == rpath2)
# True
```

#### repr()

通常の文字列の変数をエスケープシーケンスを無視（無効化）したraw文字列に変換したい場合、組み込み関数`repr()`が使える。

- [2. 組み込み関数 repr() — Python 3.6.3 ドキュメント](https://docs.python.org/ja/3/library/functions.html#repr)

```python
s_r = repr(s)
print(s_r)
# 'a\tb\nA\tB'
```

`repr()`が返すのは`eval()`に渡されたときと同じ値を持つようなオブジェクトを表す文字列であり、**先頭と末尾に`'`が付いている**。

