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

