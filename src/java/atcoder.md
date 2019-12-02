## キョウプロ全般

- 普通に`$10^9​$ のループを2 sec 以内で回せる



## 入力を受ける

### part1

```java
Scanner sc = new Scanner(System.in);
int a = sc.nextInt();  // 整数
String s = sc.next();　// 単語
String s = sc.nextline(); // 一行
```

### part2

```java
// N
// A1 A2 ... AN
// B1 B2 ... BN
// これを受け取りたい

int N = sc.nextInt();
int[] A = new int[N];
int[] b = new int[N];

for (i=0; i<N; i++){
    A[i] = sc.nextInt();
}
for (i=0; i<N; i++){
    B[i] = sc.nextInt();
}
```



### scanner メソッドの高速化

自作の関数のほうがはやい  [yu_212さん](<https://atcoder.jp/contests/abc141/submissions/7515988>)

以下テンプレ

```java
import java.io.*;
import java.util.*;

class Main {

    public static void main(String[] args) {
        MyScanner sc = new MyScanner();
        

    }

    static class MyScanner {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in), 1 << 15);
        StringTokenizer tokenizer;
    
        String next() {
            try {
                while (tokenizer == null || !tokenizer.hasMoreTokens()) {
                    tokenizer = new StringTokenizer(reader.readLine());
                }
            } catch (IOException ignored) {
            }
            return tokenizer.nextToken();
        }
    
        int nextInt() {
            return Integer.parseInt(next());
        }
    
        long nextLong() {
            return Long.parseLong(next());
        }
    }
}
```



## 出力

`System.out.println(11);`



### 整数型

| 種類       | データ型 | ビット数                                  | 値                         |
| :--------- | :------- | :---------------------------------------- | :------------------------- |
| 真偽値     | boolean  | 1ビット                                   | 真偽値,falseまたはtrue     |
| 文字型     | char     | 16ビット                                  | Unicode文字 ¥u0000～¥uFFFF |
| 整数型     | byte     | 8ビット                                   | -128～127                  |
||short      | 16ビット | -32768～32767                             |                            |
|| int        | 32ビット | -2147483648～2147483647                   |                            |
|| long       | 64ビット | -9223372036854775808～9223372036854775807 |                            |
| 浮動小数型 | float    | 32ビット                                  | 単精度浮動小数点数         |
|| double     | 64ビット | 倍精度浮動小数点数                        |                            |

int は 10^10 くらいまで  

| 整数型 | 最小値            | 最大値            |
| :----- | :---------------- | :---------------- |
| byte   | Byte.MIN_VALUE    | Byte.MAX_VALUE    |
| short  | Short.MIN_VALUE   | Short.MAX_VALUE   |
| int    | Integer.MIN_VALUE | Integer.MAX_VALUE |
| long   | Long.MIN_VALUE    | Long.MAX_VALUE    |

オーバーフローすると下みたいになる

```java
int i = Integer.MAX_VALUE;
i += 1; // i = -2147483648
```



## String 

```java
String.replaceAll("0", ""); 　    // "0"を消す
String s = String.valueOf(char)   // char to string 
String s = String.valueOf(char[]) // char[] to string 
char[] ch = str.toCharArray();    // string to char
```

### String to Int

```java
String hoge = "1";
int num = Integer.valueOf(hoge);
int num = Integer.parseInt(hoge);
```



## for 

```java
// basic
for (int i=0; i < 10; i++){
    // なんか
}

// iterable
// java 8 以降
String s = "abcd";
for (char ch: s.toCharArray()){
    System.out.println(ch);
}


```



### sort

```java
// 配列 
Integer[] a = {1, 2, 3};
Arrays.sort(a); // 昇順
Arrays.sort(a,  Comparator.reverseOrder()); // 降順

// list
List<Integer> l = new ArrayList<String>();


```

### sum

sumはない（は？？）

```java
int sum = 0;
for (i=0; i<list.length(); i++){
    sum += list[i];
}
```



## Collections

![img](C:\Users\owner\Documents\GitHub\what-I-learn\java\atcoder.assets\list.png)



### List

リストは**順序どおりに並んだ要素の集まりで重複要素を持てます**

```java
Integer[] b = new Integer[3]: // 不変長
List<Integer> l = new ArrayList<String>(); // 可変

for (int i: l){
    // hogehuga
}
```



| メソッド | 説明                                 | 記述例                   |
| :------- | :----------------------------------- | :----------------------- |
| add      | リストに値を追加                     | list.add(1)              |
| addAll   | リストにリストを追加                 | list1.add(list2)         |
| set      | リストの値を変更                     | list.set(0, 3)           |
| get      | リストの値を取得                     | list.get(0)              |
| size     | リストの要素数を取得                 | list.size()              |
| indexOf  | リストから値の要素番号を取得         | list.indexOf("a")        |
| subList  | リストから範囲を指定してコピー       | subList(1, 3)            |
| contains | リストに値が含まれるか判定           | list.contains("a")       |
| remove   | リストから指定する要素番号の値を削除 | list.remove(1);          |
| distinct | リストで重複する値を削除             | list.stream().distinct() |
| clone    | リストのコピー                       | list.clone()             |



### Set

セットの場合、**順序は無関係で要素に重複はありません**

```java 
Set<String> set = new HashSet<String>();
set.add("hello");
Collections.addAll(set, "world", "unko");
int n = set.size()
```

[リンク(そのほかmethod)](<https://www.task-notes.com/entry/20160406/1459911600>)



### Queue

| 能     | メソッド名     | 備考                                |
| :----- | :------------- | :---------------------------------- |
| 追加   | add / offer    | 容量制限がある場合は offer 推奨     |
| 取出し | remove / poll  | 空のとき 例外を起こす / null を返す |
| 参照   | element / peek | 空のとき 例外を起こす / null を返す |

```java 
Queue<Integer> queue = new ArrayDeque<Integer>();
queue.add(1);
queue.add(2);
while(true){
    Integer a = queue.poll();
    if (a==null) break;
}
```



### Deque(Stackも)

| 機能   | メソッド名        | 備考                                 |
| :----- | :---------------- | :----------------------------------- |
| 追加   | push / offerFirst | 容量制限がある場合は offerFirst 推奨 |
| 取出し | remove / poll     | 空のとき 例外を起こす / null を返す  |
| 参照   | element / peek    | 空のとき 例外を起こす / null を返す  |

```java 
Deque<Integer> stack = new ArrayDeque<Integer>();
stack.push(1);
stack.push(2);
while(true){
    Integer a = stack.poll();
    if (a == null) break;
}
```



### HashMap

```java
// key:str, value:str
HashMap<String,String> map = new HashMap<String,String>();

map.put("りんご", "apple");
map.put("ぶどう", "grapes");

if (map.containsKey("りんご")){
  System.out.println(map.get("りんご"));
}else{
  System.out.println("指定したキーは存在しません");
}
```

```java
// key; str, value; long
// https://www.sejuku.net/blog/19796

// 追加
Map型オブジェクト名.put(キー, 値);

// 取得
Map型オブジェクト名.get(キー);

```



[詳細](<http://java-code.jp/232>)



### Convert boolean to int

```java
int myInt = myBoolean ? 1 : 0;
```



## 例外処理

### try-catch

[【Java】try-catchで例外処理を実装しよう！Exceptionクラスの使い方](<https://www.sejuku.net/blog/26344>)

SQLを使うときは finally で必ずcloseするようにしよう



## 出力

複数あっても

```java
System.out.printf("%d %f ...", 引数1, 引数2, 引数3…);
```

strがほしいなら

```java
String str = String.format("変数hogeの中身は%dです。", hoge);
```



### %dみたいな書き方

| 指定子 | 主な型 | 簡単な説明       | 記述例               | 出力例   |
| ------ | ------ | ---------------- | -------------------- | -------- |
| %      | なし   | 書式指定子の開始 | なし                 | なし     |
| d      | 整数   | 10進数で出力     | printf("%d", 123)    | 123      |
| o      | 整数   | 8進数で出力      | printf("%o", 123)    | 173      |
| x      | 整数   | 16進数で出力     | printf("%x", 123)    | 7b       |
| e      | 小数   | 指数で出力       | printf("%e", 123.4f) | 1.23E+02 |
| f      | 小数   | 小数点数出力     | printf("%f", 123.4f) | 123.4    |
| s      | 文字列 | 文字列を出力     | printf("%s", “abc”)  | abc      |
| c      | 文字   | 文字を出力       | printf("%c", ‘a’)    | a        |
| b      | 真偽値 | 真偽値を出力     | printf("%b", true)   | true     |



### 桁数・左詰・0埋め・改行 ・引数番号 (※△=スペースの意味)

| 指定子 | 簡単な説明           | 記述例                                           | 出力例         |
| ------ | -------------------- | ------------------------------------------------ | -------------- |
| 数     | 最小桁数を指定       | printf("[%5d]", 123)                             | [△△123]        |
| .数    | 文字列の最大幅を指定 | printf([%.3s]", "abcde")                         | [abc]          |
| -      | 左詰                 | printf([%-5s]", "abc")                           | [abc△△]        |
| 0      | 0埋め                | printf("[%05d]",123);                            | [00123]        |
| n      | 改行                 | printf("abc%ndef");                              | abc def        |
| 数$    | 引数の番号           | printf( "%3$s,%2$s,%1$s", "str1","str2","str3"); | str3,str2,str1 |



### 日付 (※日時は2018年1月5日 17時4分5秒を想定)

| 指定子 | 簡単な説明        | 記述例                     | 出力例     |
| ------ | ----------------- | -------------------------- | ---------- |
| tY     | 年(4桁)           | printf("%tY", new Date()); | 2018       |
| ty     | 年(2桁)           | printf("%ty", new Date()); | 18         |
| tm     | 月(2桁)           | printf("%tm", new Date()); | 01         |
| td     | 日(2桁)           | printf("%td", new Date()); | 05         |
| te     | 日(1~2桁)         | printf("%te", new Date()); | 5          |
| tH     | 時(2桁)24時間制   | printf("%tH", new Date()); | 17         |
| tl     | 時(1~2桁)12時間制 | printf("%tl", new Date()); | 5          |
| tM     | 分(2桁)           | printf("%tM", new Date()); | 04         |
| tS     | 秒(2桁)           | printf("%tS", new Date()); | 05         |
| tF     | 日付              | printf("%tF", new Date()); | 2018-01-05 |
| tT     | 時刻              | printf("%tT", new Date()); | 17:04:05   |





## マラソンメモ

### 時間の計測

[Java.lang.System.currentTimeMills()](<https://www.tutorialspoint.com/java/lang/system_currenttimemillis.htm>)

```java
final long TIME_LIMIT = 5500;
long st = System.currentTimeMillis();
long et = st + TIME_LIMIT;

while (System.currentTimeMillis() < et) {
    // hoge
}
```



### ファイルを開く

```java 
try (FileInputStream reader = new FileInputStream(dir + filename1);
     FileOutputStream writer = new FileOutputStream(dir + filename2)){
    
    writer.write(0);
    
} catch (IOException e) {
    e.printStackTrace();
}finally{
     //finally句でのリソースのcloseは不要
    // try{
    // 	if (reader!=null){ reader.close(); }		
}
```





### 読みたい

[競プロだけでは習得しづらいJava Stream API 【アドベントカレンダー 6日目】](<chttps://trap.jp/post/551/>)

[貪欲法、山登り法、焼きなまし、ビームサーチ、これらの間の関係について](<https://kimiyuki.net/blog/2019/03/07/local-search-and-greedy/>)

