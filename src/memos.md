# memos

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