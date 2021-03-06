## 主要なファイル

（**[View] > [Tool Windows] > [Project]** を選択して）[**Project**] ウィンドウを確実に開き、そのウィンドウの上部のプルダウン リストから [**Android**] ビューを選択します。この操作で次のファイルが表示されます。

- **app > java > com.example.myfirstapp > MainActivity**

  メイン アクティビティ（アプリのエントリ ポイント）。アプリをビルドして実行すると、システムにより `Activity` のインスタンスが起動され、そのレイアウトが読み込まれます。

- **app > res > layout > activity_main.xml**

  アクティビティの UI のレイアウトを定義する XML ファイル。「Hello world!」という `TextView` 要素が含まれています。

- **app > manifests > AndroidManifest.xml**

  [マニフェスト ファイル](https://developer.android.com/guide/topics/manifest/manifest-intro.html?hl=JA)にはアプリの基本的な特徴が記述され、アプリの各コンポーネントが定義されています。

- **Gradle Scripts > build.gradle**

  この名前のファイルは 2 つあり、1 つはプロジェクト（「Project: MyFirstApp」）用でもう 1 つは「アプリ」モジュール（「Module: app」）用です。各モジュールに独自の `build.gradle` ファイルが含まれますが、このプロジェクトには現在、モジュールが 1 つだけあります。ほとんどの場合、モジュールの `build.gradle` ファイルを使用して Gradle ツールでアプリをコンパイルしてビルドする方法を設定します。このファイルについて詳しくは、[ビルドを設定する](https://developer.android.com/studio/build/index.html?hl=JA)をご覧ください。

  

## アプリのコンポーネント

アプリのコンポーネントは Android アプリに不可欠な構成要素です。各コンポーネントは、システムやユーザーがアプリに入るエントリ ポイントになります。一部のコンポーネントは他のコンポーネントに依存しています。

アプリのコンポーネントには 4 つのタイプがあります。

- アクティビティ
- サービス
- ブロードキャスト レシーバ
- コンテンツ プロバイダ

各タイプは異なる目的を果たし、コンポーネントの作成方法や破棄方法を定義するライフサイクルもそれぞれ異なります。

[詳細](<https://developer.android.com/guide/components/fundamentals.html?hl=JA#DeclaringComponents>)

## 設定

[Android Studio の設定](<https://developer.android.com/studio/intro/studio-config?utm_source=android-studio#antivirus-impact>)



## IDE

### ファイルの依存関係

[class名を選択] -> [右クリック] -> [Go to ] -> [Declarement]

これでそのクラスをnewしたり宣言している他のファイルに飛べる





## エラーログ

### error: failed linking file resources.

layout と string でうまくマッチしていない or activity とマッチしていないidがある



### （sqlite で）エラーなく落ちる

DBのキーの名前などを間違えている



### error: XML or text declaration not at start of entity.

XML file のはじめに空白や改行，コメントがある



### error: app:transformDexWithInstantRunSlicesApkForDebug

[stackoverflow](<https://stackoverflow.com/questions/55848601/gradle-crashes-in-apptransformdexwithinstantrunslicesapkfordebug>)

This can be fixed by updating to Gradle 5.4
The easiest way to do this is to update the wrapper in use:

- Open `gradle/gradle-wrapper.properties`
- Find the line that looks like

```java
distributionUrl=https\://services.gradle.org/distributions/gradle-5.4-all.zip
```

- Change the version to 5.4
  Then try running the build again.
  Another way to fix this is to disable instant run. Go to File -> Settings -> Instant Run and then uncheck the box (or use preferences for Mac users).



### error: 'try' can use automatic resource management 

```java
try {
    DataBaseHelper db = ...;
    書き込んだり読み込んだり
} finally {
    db.close();
}
```

try-with-resource 文にしたら`finally` でcloseしなくてよい

```
try (DataBaseHelper db = ...) {
    書き込んだり;
}
```

[try-with-resources文の基本](<https://qiita.com/Takmiy/items/a0f65c58b407dbc0ca99>)



### ネットワーク権限を付与したのにapiを叩けない．エラーもない

### D/NetworkSecurityConfig: No Network Security Config specified, using platform default

Android 9(pi) ではHTTP通信などが無効化されている．許可する場合は別途xmlを指定する[参考](<https://qiita.com/b_a_a_d_o/items/afa0d83bbffdb5d4f6be>)



