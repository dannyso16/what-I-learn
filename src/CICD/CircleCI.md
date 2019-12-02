# Circle CI で Hello World するまで

https://qiita.com/tatane616/items/8624e61473a9957d9a81

基本これを参考にやった．詰まったところをメモ．
<br>

## `.circleci/config.yml` をコミットした後エラーが出た

![error](.\CircleCI.assets\error.PNG)

エラーを見てみると，

```
Configuration errors: 2 errors occurred:

* Configuration version 2.1 requires the "Enable Pipelines" project setting. Enable pipelines under Project Settings -> Advanced Settings. In order to retrigger pipelines, you must push a new commit.
* Cannot find a job named `build` to run in the `jobs:` section of your configuration file.
If you expected a workflow to run, check your config contains a top-level key called 'workflows:'
```

一つ目で言われてる設定を見ても，enable になってるし，二つ目のエラーも top-level に workflows を置かなくてもいいはず…．

結論は，**このエラーは別に問題ではない**ようだ．ここで CI の設定をしているので，次のコミットから反映される，つまり次に新しいコミットをすると`Hello world`できる．

![new_commit](.\CircleCI.assets\new_commit.PNG)

詳細を見てみると，

![hello_circle_ci](.\CircleCI.assets\hello_circle_ci.PNG)

できた！！
<br>

## 次

Markdwon を勝手にpdf に変換するようにしていきたい．
<br>



## 参考

[MarkdownをCircleCI上でPDFに変換してGoogleドライブにデプロイする]( https://tech.quartetcom.co.jp/2018/05/14/markdown-pdf-circleci-googledrive-deployment/ )
：これやりたい。2018/05 の記事

[GitHub+CircleCI入門]( https://qiita.com/tatane616/items/8624e61473a9957d9a81 )
：やってみた系。hello worldするのに一度fresh commit が必要

[いまさらだけどCircleCIに入門したので分かりやすくまとめてみた]( https://qiita.com/gold-kou/items/4c7e62434af455e977c2 )
：網羅的。ちょっと事前知識がないと難しい…

