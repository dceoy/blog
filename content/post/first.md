+++
date = "2015-04-30T00:53:48+09:00"
draft = true
title = "Hugo でブログを作った"
tags = ["Hugo", "Go"]

+++

以前, はてなブログで Web 関連の技術ブログを書いていたが, 無料プランでは広告が出るので自分でビルドした.

使用したのは Go で書かれた [Hugo](http://gohugo.io/) という静的サイトエンジン.  
他のツールと比較して記事の生成速度に優れている.

Go の環境があれば以下でインストールできる.

```sh
$ go get -v github.com/spf13/hugo
```

ブログ作成に際し, 知り合いのエンジニアが使っていた Python 製 [Sphinx](http://sphinx-doc.org/) ベースの [Tinkerer](http://tinkerer.me/) というツールにも興味を持ったが, reST でなく Markdown で書きたいので別のものを探した.  

当初, 過去に試したことがあった Ruby 製の [Octopress](http://octopress.org/) を考えたが, [Hugo に移行した人のブログ記事](http://deeeet.com/writing/2014/12/25/hugo/)を読んで結局こちらに落ち着く.

Hugo は操作性はシンプルで不満もないが, 選択できるテーマが少ないのは難点.  
デザインを気にするならテーマも自分で書いた方がいいのかもしれない.
