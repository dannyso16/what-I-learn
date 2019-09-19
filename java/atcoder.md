## 入力を受ける

```java
Scanner sc = new Scanner(System.in);
int a = sc.nextInt();  // 整数
String s = sc.next();　// 単語
String s = sc.nextline(); // 一行
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



### sort//

```java
// 配列 
Integer[] a = {1, 2, 3};
Arrays.sort(a); // 昇順
Arrays.sort(a,  Comparator.reverseOrder()); // 降順

// list
List<Integer> l = new ArrayList<String>();


```



## Collections

![img](C:\Users\owner\Documents\GitHub\what-I-learn\java\atcoder.assets\list.png)



### List

```java`

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

### Queue

### Deque



### Dictionary