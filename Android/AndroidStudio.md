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

​		