+++
date = "2015-05-11T23:56:03+09:00"
draft = true
title = "[R] ggplot2 で描く forest plot"
tags = ["ggplot2", "r", "visualization", "statistics"]

+++

forest plot は, オッズ比や相対リスクの点推定値と信頼区間を順に並べる描画方法で, [meta-analysis](http://www.med.osaka-u.ac.jp/pub/kid/clinicaljournalclub8.html) の可視化にしばしば用いられる.

これを R で簡潔に描くライブラリを探したが, 使い易いものがなかったので [ggplot2](http://ggplot2.org/) でコードを書いた.

ggplot2
-------

合理的に美麗なグラフを描ける R のパッケージ.  
人気があるライブラリで使ってる R ユーザーも多いと思う.

多様なグラフを統一的なインターフェースで作成できる.

forest plot using ggplot2
-------------------------

複数のオッズ比の点推定値と信頼区間の図示に主眼を置いた.  
meta-analysis では, 各研究の重みや菱型で表す統合オッズ比などを含めるケースもあるが, 自分の用途では必要なかったのでそれらは対応していない.

以下は描画コードと読み込むオッズ比のサンプル.

<script src="https://gist.github.com/dceoy/a3c63540a8722afbc4dd.js?file=forest_plot.R"></script>
<script src="https://gist.github.com/dceoy/a3c63540a8722afbc4dd.js?file=odds_ratio.csv"></script>

ggplot2 は forest plot を想定した関数は備えていないようだったので, 点と区間を表現する `geom_pointrange` を使った.  
オッズ比のサンプルは[以前書いた Fisher exact test の記事と同じ方法](/post/row_fisher_test/)で作った.

下図は出力された SVG.

<div style="text-align: center;">
  <img src="https://rawgit.com/dceoy/a3c63540a8722afbc4dd/raw/plot.svg" alt="plot">
</div>
<br>

まとめ
------

比較的簡単に書けた.  
ただ, 重みや統合オッズ比まで必要な場合は meta-analysis のパッケージを利用した方が無難かもしれない.

このコードを最初に書いた 2014 年春頃は forest plot 専用のパッケージを見かけなかったが, 最近は[あるらしい](http://cran.r-project.org/web/packages/forestplot/vignettes/forestplot.html).

<div style="text-align: center;">
  <iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=dceoy-22&o=9&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=4873116538" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>
</div>
<br>
