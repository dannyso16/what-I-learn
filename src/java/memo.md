## ERR

### XXX cannot be resolved to a variable
XXXを import できていない
もしくはimport もとがおかしい

### XXX cannot be resolved to a type

XXX の型が何かおかしい

1. 必要なクラスがimportできていない
2. 引数と渡す値の型があってない

### 例外をStringで受け取りたい

```java
import java.io.*;

try{
    doSomething();
} catch (IOException exception) { 
    System.out.println(exception.getMessage()); 
    System.out.println(exception.toString()); // same above     
```

###  java.lang.Error　[リンク](http://www.tokoro-lab.org/person/suda/japi/java.lang.Error.html)

今回はimport したクラス名のtypoが原因だった

Error は発生するべきでない異常なイベントのための Throwable のサブタイプである。 何を行っているか確信がない限り、 Error を捕えようとしてはいけない。具体的でないのでやっかいだ…

以下記事抜粋[初心者がよく出会うエラーと対策7つ](https://eng-entrance.com/java-basic-error)





## Swing (GUI application)

[Swingを使ってみよう](https://www.javadrive.jp/tutorial/)
：結構詳細に載ってる

[**SwingでJavaに強くなる** itmedia 連載](https://www.atmarkit.co.jp/ait/articles/0605/31/news125.html)
：全部で6回で全体がつかめる

[JFrame(画像の表示](http://java-study.blog.jp/archives/1021357687.html)

[BoxLayoutは縦方向又は横方向にコンポーネントを並べて配置できる](https://www.javadrive.jp/tutorial/boxlayout/index2.html)

[Java入門 (9) - タイマーとスレッド](https://codezine.jp/article/detail/2597)
：わかりやすい．この連載読んでもいいかも

### [複数行テキスト](http://wisdom.sakura.ne.jp/system/java/swing/swing46.html)

### JTextAreaで文字色を変える
[リンク](https://stackoverflow.com/questions/9650992/how-to-change-text-color-in-the-jtextarea)

### 縦に並べる

```java
JPanel p = new JPanel();
p.setPreferredSize(new Dimension(200, 100));
p.setBackground(Color.ORANGE);
p.setLayout(new BorderLayout());

JButton btn1 = new JButton("NORTH"); // 上
JButton btn2 = new JButton("SOUTH"); // 下
p.add(btn1, BorderLayout.NORTH);
p.add(btn2, BorderLayout.SOUTH);
contentPane.add(p);
```






### カレントディレクトリがほしいい
```java
String pwd = System.getProperty("user.dir");
System.out.println(pwd);
```
### 時間の計測
```java
long startTiem = System.currentTimeMills();
// some process
long endTimek = System.currntTimeMills();

System.out.println(endTime - startTime + "ms");
```

### タイマー
[Java入門 (9) - タイマーとスレッド](https://codezine.jp/article/detail/2597)


```java
class TimeLabel extends JLabel {
    private DateFormat format;
    
    public TimeLabel(){
        this.setFont(new Font("Dialog",Font.BOLD,24));
        format = new SimpleDateFormat("HH:mm:ss");
        Timer t = new Timer();
        t.schedule(new TimerLabelTask(), 0,1000);
    }
    
    public void setTime(){
        Calendar calendar = Calendar.getInstance(Locale.JAPAN);
        this.setText(format.format(calendar.getTime()));
    }
    
    class TimerLabelTask extends TimerTask {
        
        public void run(){
            setTime();
        }
   
```



### 外部プロセス呼び出し

[外部プロセス起動](https://www.ne.jp/asahi/hishidama/home/tech/java/process.html#ProcessBuilder)

JDK1.4まではRuntimeクラスだったが，いまはProcessBuilderでいい．（Runtimeも内部はProcessBuilderになってる）

~~もう少し手元で試して，追記してくれ~~ 　←動かした

```java
// cited by : http://m-miya.blog.jp/archives/1065088079.html
BufferedReader br = null;
        // 起動するコマンド、引数でProcessBuilderを作る。
        ProcessBuilder pb = new ProcessBuilder("./aaa.sh", "arg0", "arg1");
        // 実行するプロセスの標準エラー出力を標準出力に混ぜる。
	    // (標準エラー出力を標準入力から入力できるようになる)
        pb.redirectErrorStream(true);
        try {
            // プロセス起動
            Process process = pb.start();
            
            // 起動したプロセスの標準出力を取得して表示する。
            //   標準出力やエラー出力が必要なくても読んどかないとバッファがいっぱいになって
            //   プロセスが止まる(一時停止)してしまう場合がある。
            InputStream is = process.getInputStream();
            br = new BufferedReader(new InputStreamReader(is));
            while(true) {
                String line = br.readLine();
                if(line == null) {
                    break;
                }
                System.out.println(line);
            }
            // プロセスの終了を待つ。
            int ret = process.waitFor();
            // 終了コードを表示
            System.out.println("ret = " + ret);
        } catch (IOException ex) {
            Logger.getLogger(TestProcess.class.getName()).log(Level.SEVERE, null, ex);
        } catch (InterruptedException ex) {
            Logger.getLogger(TestProcess.class.getName()).log(Level.SEVERE, null, ex);
        } finally {
            if(br != null) {
                try {
                    br.close();
                } catch (IOException ex) {
                    Logger.getLogger(TestProcess.class.getName()).log(Level.SEVERE, null, ex);
                }
            }
        }
```



[Javaでのプロセス・スレッドについて勉強したまとめ](https://www.techscore.com/blog/2018/12/13/java-process-thread-study/)
：結構網羅的，やってみよう

### ゼロ埋め

```java
String.format(書式文字列, 値);
```

- 第1引数：値をどのような書式(形式)で出力するかを指定します。例えば5桁で0埋めしたい場合は次の書式文字列を指定します。
  - %05d
    - %・・・書式文字列であることを表す指示子
    - 0・・・埋める文字。この場合ゼロ
    - 5・・・桁数。この場合5桁
    - d・・・出力する値の型。この場合整数(decimal)
- 第2引数：出力する値を指定します。今回は数値を0埋めするので、「1」「12」「9234」などの数値を指定することになります。

[リファレンス](https://docs.oracle.com/javase/jp/8/docs/api/java/util/Formatter.html#syntax)

