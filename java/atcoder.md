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

- String.replaceAll("0", ""); // "0"を消す



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



### Dictionary

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

[詳細](<http://java-code.jp/232>)



### 読みたい

[競プロだけでは習得しづらいJava Stream API 【アドベントカレンダー 6日目】](<chttps://trap.jp/post/551/>)