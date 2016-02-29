+++
date = "2015-05-09T13:57:52+09:00"
draft = true
title = "Gist に置いた HTML を Web ページとして表示する"
tags = ["github", "html", "css", "javascript", "web"]

+++

<div style="text-align: center;">
  <img src="../../images/gist.png" alt="logo">
</div>
<br>

少し前まで JavaScript や CSS, SVG のちょっとしたコードを埋めた HTML のデモを GitHub Pages のリポジトリに置いていたが, ブログを走らせるようになったので場所を Gist に移した.  
Gist に置いた HTML は [RawGit](https://github.com/rgrove/rawgit) を利用すると Web ページとして表示できる.

RawGit
------

GitHub や Gist に置いた HTML や JavaScript の raw ファイルを, 適当な content type で供給するサービスで, CDN のように使うことが可能.

ファイルへのリンクは [rawgit.com](https://rawgit.com/) のフォームから作成する.  
以前は rawgithub.com というドメインだった.

今回 Gist に移したコード
------------------------

- Accordion Menu --- [demo](https://rawgit.com/dceoy/bec35d51cffe05929a39/raw/accordion.html) / [gist](https://gist.github.com/dceoy/bec35d51cffe05929a39)  

> CSS と jQuery で作った, 画像を使わない Accordion Menu.

- Word Clouds --- [demo](https://rawgit.com/dceoy/71b175c0b0f612927995/raw/d3_word_clouds.html) / [gist](https://gist.github.com/dceoy/71b175c0b0f612927995)  

> [D3](http://d3js.org/) と [d3-cloud](https://github.com/jasondavies/d3-cloud) で動く Word Clouds のデモ.  
> サンプルデータの CSV と JavaScript も rawgit.com 経由で読み込ませている.

まとめ
------

リンクの作成のみで Web ページとして見れる.  
Gist は簡単に使えてリビジョンも付くので, Web デザイナーの人にも有用かもしれない.


<script>
  amzn_assoc_default_search_key = "cdn";
</script>
