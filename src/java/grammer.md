# Grammer

## String

### 分割

```java
String str = "りんご,,すいか,";
String[] fruit = str.split(",", 0);
// fruit[0] = "りんご";
// fruit[1] = "";
// fruit[2] = "すいか";
```

第二引数は分割回数で`-1`で分割の制限がない．また0の場合，分割の最後の項目が空白の場合にはそれを配列に格納しない．



## パスからファイル名を取得

```java
import java.io.File;
String fileName = new File("C:\\temp\\hello.txt").getName();
```





## 実行コマンド

### jar

[jar入門](https://qiita.com/hiwm0126/items/1b3c008c21463d78337a)

**jar**とは、コンパイルされた複数のclassファイルおよびそれが使用する画像などのリソースを一つにまとめZIP形式で圧縮されたファイル、もしくはそれを出力するツールのことを言います。**Java Archive**の略です。

圧縮することでJavaのライブラリやアプリケーションの配布、利用が簡単になります。jarはコマンドでよく使用されます。

```
javac App.java
jar -cvf App.jar *.class
```



## javadocの書き方

[Javadocの基礎知識](https://qiita.com/sudahiroshi/items/f12837648304bbf00a24)

### javadocとは

[javadox公式](http://java-code.jp/49)

javadocとは，「ドキュメントを作るのが面倒なので，プログラム中に特定のルールに従って付けたコメントを抽出してドキュメントを作っちゃう」考え方に沿って，Java言語のソースコードからドキュメントを生成する仕組みです．これにより，ドキュメントファイルを紛失することも無くなります．　jdkに付属してる

### 書き方

- @author: プログラム制作者
- @version: 
- @param: メソッドパラメータ
- @return: 返り血
- 他もある

