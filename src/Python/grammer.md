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

