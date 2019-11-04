# AtCoder memo

## 基本文法

とりあえず[これ](<https://access-company.github.io/kotlin_intro/basic_syntax.html>)見ろ

概要は[３０分で覚えるKotlin文法](<https://qiita.com/k5n/items/cc0377b75d8537ef8a85#for>)

### 宣言

val: 不変の変数（初期値から変更不可能）

var: 変更可能

```kotlin
val N: Int = 0
N = 100 // error: val cannot be reassigned
var a: String = "hello"
a = "hel" // ok
```



### 数値

、数値は読みやすさ向上のために任意の位置に `_` を補った書き方ができる

`val int_max: Int = 2_147_483_674`



### 型

`Unit`: ない（java のvoid）

```kotlin
// 返り血がない
fun hoge(): Unit {
    print(11)
}
```



### 関数

```kotlin
fun twice(x: Int): Int {
    return x*2
}

fun 関数名(引数: 型, .., 引数: 型 = デフォルト値, ...) {
}
```

Kotlinでは関数はファイルのトップレベルで宣言できる，つまりjavaみたいに関数を入れるためのクラスがなくても定義できる

### クラス

[リファレンス](<https://dogwood008.github.io/kotlin-web-site-ja/docs/reference/classes.html>)

クラスのインスタンスはトップレベルではだめ

```kotlin
class Hoge(val a: Int, ...) {
    ...
}

Hoge().method() // error: expecting a top level declaration
```

メイン関数内にかく

```kotlin
class Hoge(val a: Int, ...) {
    ...
}

fun main(args: Array<String>){
    Hoge().method() 
}
```

initの初期化

```kotlin
class Customer(name: String) {
    val customerName = name // 受け取れる
    var list = mutableListOf<Int>() // リストの初期化はinitで
    
    // 初期化はinitで
    init {
        logger.info("Customer initialized with value ${name}")
        listの初期化
    }
}
```





## 入力

### 一文字

javaみたいにScannerが使える

```kotlin
import java.util.*

fun main() {
    val scanner = Scanner(System.`in`)
    val n = scanner.nextInt()
}
```

kotlinライクだとreadLine()もあるよ

### 配列

```kotlin
var d = mutableListOf<Int>()
for (i in 1..N) {
    val di: Int = sc.nextInt()
    d.add(di)
}
```