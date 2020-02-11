# memos

# TOC

[toc]



# 未分類

## prop と eVar

カスタムトラフィック変数（prop（s.prop）またはプロパティ変数とも呼ばれます）は、各変数が Analytics に送信された回数をカウントするカウンターです。

割り当てる変数のタイプや場所を判断する際は、prop と eVar の機能性の違いを理解していることが重要です。これらの違いを理解していれば、最適の変数のタイプを判断できます。詳しくは、「 [Prop と eVar の比較 ](https://docs.adobe.com/content/help/ja-JP/analytics/implementation/analytics-basics/traffic-props-evars/props-vs-evars.translate.html)」を参照してください。

また、prop は、カスタムデータを特定のトラフィック関連イベントに相互に関連付けることができます。これらの変数は、Web サイトの各ページの Analytics コードに埋め込まれます。 は、s.propAnalytics 変数を使用して、組織、産業、およびビジネス目標に特有のカスタムレポートの作成を可能にします。

例えば、自動車メーカーでは、「ページ」レポートを完成させるために「最も人気のある車種」を把握したい場合があります。これをおこなうには、トラフィックプロパティの 1 つを割り当てて、車種を表します。次に、適切なページで車種を渡すコードを導入します。

prop は、パスレポートやクロス集計レポートで使用されます。例えば、プロパティ変数を使用して、コンテンツタイプ、サブセクションまたはテンプレート名を示すことができます。作成されるカスタムトラフィックレポートには、最も頻繁に閲覧されるコンテンツタイプ、サブセクションまたはテンプレートが示されます。

[Adobe Analytics 用語みたい]( https://docs.adobe.com/content/help/ja-JP/analytics/implementation/analytics-basics/traffic-props-evars/props-evars.translate.html )



## Windows のユーザーフォルダのパス

 `C:\Users\(ユーザー名)\Documents` は，ユーザ名によって変わる．

`%userprofile%\Documents` とすればいい．



## VS Code で Analyzing in backgroudn となり，、メモリバカ食いしてファンうなる


![python_analysing_background](.\memos.assets\python_analysing_background.png)

解決作

>You can disable the new Python Language Server by opening settings in VSCode (Ctrl+, ) and set "python.jediEnabled": true. Then reload the window and/or restart VSCode.

自分の場合 [ctrl +]が拡大だったので，設定からいじったら今のところ大丈夫だ．

Microsoft Python Langage Server がやたら思いので，Jediが使い勝手がいいようだ．

> High memory usage： https://github.com/Microsoft/python-language-server/issues/832 Jedi is an autocompletion tool for Python that can be used in IDEs/editors. Jedi works. Jedi is fast. It understands all of the basic Python syntax elements including many builtin functions. So you can switch Jedi instead of Python Language Server.
>
> Process:
>
> set "python.jediEnabled": true
>
> disable the Visual Studio IntelliCode plugin
>
> delete the .vscode directory
> 



## onClickButton or onButtonClick??

検索回数は

- “onButtonClicked” returns ~22,000 search results
- “onClickedButton” ~608 results
- **“onButtonClick" ~122,000,**
-  “onClickButton" ~27,600

[参考](https://stackoverflow.com/questions/56051358/function-name-onbuttonclick-or-onclickbutton)



## Windwos 10 レジストリ設定

[Windows 10のレジストリ設定の基本 thickIT](https://thinkit.co.jp/story/2015/06/30/6147)

[Pythonでレジストリを操作する（PySideのQSettingsから）](https://note.com/it_ks/n/nb5988c7187d7)

[上級ユーザー向けの Windows レジストリ情報 microsoft](https://support.microsoft.com/ja-jp/help/256986/windows-registry-information-for-advanced-users)



## Windows.old 

[消す](https://thinkit.co.jp/story/2015/10/26/6516)



### 右クリックのコンテンツ編集

[あなただけの右クリックで、ストレスフリーな開発を。(コンテキストメニュー編集マニュアル)]([https://qiita.com/NumLocker/items/f8016f1aed7207b850fb#2%E7%AB%A0-%E3%83%95%E3%82%A9%E3%83%AB%E3%83%80%E3%81%A7%E3%81%AE%E5%8F%B3%E3%82%AF%E3%83%AA%E3%83%83%E3%82%AF](https://qiita.com/NumLocker/items/f8016f1aed7207b850fb#2章-フォルダでの右クリック))

[ディレクトリの右クリックメニューにコマンドプロンプトを表示させる(暫定)](https://www.pg-fl.jp/program/tips/w10bgcmd.htm)

## powershell

### 二階層上のパスに移動したい

```po
$RootPath = Split-Path (Split-Path $PSScriptRoot -Parent) -Parent
```

### printする

```
$word='PowerShell'; Write-Output "Windows $word"
```



# Markdown記法（Typora編）

## ToC(Table of Content)目次がほしい

`[toc]`と打つだけ！！





# ffmpeg

Google Colaboratoryでは標準で使える。複数の画像をgifにまとめたり、動画化できる。アニメーション生成はコードを書くよりこっちのが楽な印象。



## [連番画像からGIFアニメを生成する](http://kimizuka.hatenablog.com/entry/2018/05/26/204618)

0.png、1.png、2.png、3.pngという感じの連番画像をGIFアニメにしたいとき、

```bash
fmpeg -i %d.png -vf palettegen palette.png
```

と、まずpalette.pngをつくり、

```bash
ffmpeg -f image2 -r 1 -i %d.png -i palette.png -filter_complex paletteuse anim.gif
```

とカラーパレットをもとにGIFアニメをつくれます。

`r = 1` のところがFPSになるので、上記の通りだと、連番の枚数がそのままGIFアニメの秒数になります。
また、事前にすべての画像の幅、高さを統一しておく必要があります。

例えば、`hoge_001.png`のように三桁0うめにしてる時は

```bash
hoge_%03d.png
```

のように指定すればいい。

ちなみにpythonだと0うめは `str.zfill(keta-suu)`を使うといい

```python
 plt.savefig("hoge_{}.png".format(str(iteration).zfill(3)))
```

