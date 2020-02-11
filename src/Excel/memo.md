# メモ

**Excelのマクロとか書けるようにしようぜ！！**



## 列を固定したい

スライドしても常に同じ場所に表示させるやつ

[表示]→[列を固定]



## IF

`=IF(式, TRUEの処理, FALSEの処理)`

### 空白なら計算しない

`= IF(A1="", "", A1+1)`

長いので`$""`をつけるもあり[リンク](https://www.excelspeedup.com/kuuhakuif/)



### 空白かどうかの確認→ISBLANK(ほげ)



## 切り捨てなど

### ROUNDDOWN(値，３)

少数３桁できりすて

### INT(値)



# 日時関係

## 今日の日付の行の色を強調

1. 区間を選択し、右クリック
2. 条件書式設定
3. カスタム数式
4. `=$A1=today()`

## 今週の月曜？？

エクセルは**日曜始まり**

**![20191106180709](C:\Users\HOME\Documents\GitHub\what-I-learn\src\Excel\memo.assets\20191106180709.jpg)**

日付（シリアル値）から1を引いて、その数を7の倍数で切り捨てる

→　日曜～金曜については直前の土曜日を返し、土曜については7日前の土曜日を求めることができます

以下参考までに

- 先週日曜日：=FLOOR(TODAY()-1,7)-6
- 先週月曜日：=FLOOR(TODAY()-1,7)-5
- 先週火曜日：=FLOOR(TODAY()-1,7)-4
- 先週水曜日：=FLOOR(TODAY()-1,7)-3
- 先週木曜日：=FLOOR(TODAY()-1,7)-2
- 先週金曜日：=FLOOR(TODAY()-1,7)-1
- 先週土曜日：=FLOOR(TODAY()-1,7)
- 今週日曜日：=FLOOR(TODAY()-1,7)+1
- 今週月曜日：=FLOOR(TODAY()-1,7)+2
- 今週火曜日：=FLOOR(TODAY()-1,7)+3
- 今週水曜日：=FLOOR(TODAY()-1,7)+4
- 今週木曜日：=FLOOR(TODAY()-1,7)+5
- 今週金曜日：=FLOOR(TODAY()-1,7)+6
- 今週土曜日：=FLOOR(TODAY()-1,7)+7
- 来週日曜日：=CEILING(TODAY(),7)+1
- 来週月曜日：=CEILING(TODAY(),7)+2
- 来週火曜日：=CEILING(TODAY(),7)+3
- 来週水曜日：=CEILING(TODAY(),7)+4
- 来週木曜日：=CEILING(TODAY(),7)+5
- 来週金曜日：=CEILING(TODAY(),7)+6
- 来週土曜日：=CEILING(TODAY(),7)+7



## あと何日?

`=DAYS(最終日、今)`

例、=DAYS("2020/04/19", TODAY())

