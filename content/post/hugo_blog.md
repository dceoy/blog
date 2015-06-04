+++
date = "2015-04-30T00:53:48+09:00"
draft = true
title = "Hugo でブログを作った"
tags = ["hugo", "go", "wercker", "ci", "github"]

+++

<div style="text-align: center;">
  <img src="../../images/hugo.png" alt="logo">
</div>
<br>

以前, はてなブログで Web 関連の技術ブログを書いていたが, 無料プランでは広告が出るので自分でビルドした.

作成に際し, 知り合いのエンジニアが使っていた Python 製 [Sphinx](http://sphinx-doc.org/) ベースの [Tinkerer](http://tinkerer.me/) というツールにも興味を持ったが, reST でなく Markdown で書きたいので他のものを探した.  
当初, 過去に試したことがあった Ruby 製の [Octopress](http://octopress.org/) を考えたが, [移行した人のブログ記事](http://deeeet.com/writing/2014/12/25/hugo/)を読んで, 最終的に [Hugo](http://gohugo.io/) を使うことにした.

Hugo
----

Go で書かれた静的サイトエンジン.  
他のツールと比較して記事の生成速度に優れている.

Go の環境があれば以下でインストールできる.

```sh
$ go get -v github.com/spf13/hugo
```

Mac OS X では Homebrew からもインストール可能.  
また, バイナリでも配布されている.

記事は Markdown で書き, ビルドインサーバーでプレビューできる.

Wercker CI
----------

ブログのホストには GitHub Pages を利用し, [公式のチュートリアル](http://gohugo.io/tutorials/automated-deployments/)を参考に, [Wercker CI](http://wercker.com/) でデプロイまで自動化した.  
リポジトリが GitHub に push されると HTML をビルドし, プロジェクトページの branch にデプロイする仕組み.

Wercker は [Travis CI](https://travis-ci.org/) や [CircleCI](https://circleci.com/) のような SaaS 型の CI サービスで, 現時点では GitHub や Bitbucket のプライベートリポジトリでも使用可.  
CI の設定は `wercker.yml` に記述してリポジトリの root に置く.

まとめ
------

Hugo はビルドも速く, 操作もシンプルで使いやすい.  
また, Wercker で自動化してからは push するだけで更新されるようになったので, かなり利便性が向上した.

ただし, 使えるテーマはまだ少ないので, デザインを気にするなら自分で書いた方がいいかもしれない.


<script>
  amzn_assoc_default_search_key = "github";
</script>
