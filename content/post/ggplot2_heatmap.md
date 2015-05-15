+++
date = "2015-05-14T23:52:26+09:00"
draft = true
title = "[R] ggplot2 で描く heatmap"
tags = ["ggplot2", "r", "visualization"]

+++

heatmap は比較的メジャーな可視化方法なので, 使える R のパッケージも多い.  
ggplot2 でも矩形を敷き詰める `geom_tile` で heatmap のような表現が可能になる.

heatmap using ggplot2
---------------------

以下は描画コードと値のサンプル.

<script src="https://gist.github.com/dceoy/5f3d99084d604b847447.js?file=heatmap.R"></script>
<script src="https://gist.github.com/dceoy/5f3d99084d604b847447.js?file=matrix.csv"></script>

サンプルのデータはシェルから以下のワンライナーで作った.

```sh
$ echo 'row,col,val' > matrix.csv
$ seq -w 0 55 | grep -v '[6-9]' | sed -e 's/\(.\)\(.\)/\1 \2/g' | awk '{ print "row"$1",col"$2","exp(rand() * 10) }' >> matrix.csv
```

heatmap を表現するとき, 図に対応した行数・列数の元データから作成するケースは少なくないと思うが, ggplot2 では, 行列の位置と値をレコードとして持つテーブルから作図する.  
前者はスプレッドシートからの移植性などには優れるものの, 図の列が増えたときに元データが横に広がって処理が煩雑になるが, 後者はそうした心配がない.

下図は出力された SVG.

<div style="text-align: center;">
  <img src="https://rawgit.com/dceoy/5f3d99084d604b847447/raw/plot.svg" alt="plot">
</div>
<br>

まとめ
------

元データが位置と値のテーブルになる点は良いと思う.  
この形式は SQL で抽出してきたデータを扱うとき, かなり有利になる.

R には heatmap と同時にクラスタリングを行うパッケージもあるが, そうしたものには対応していない.  
(もっとも, 個人的にはデータ処理と可視化は分離すべきだと思うので, 同時に行う方が邪道な気もする.)

<div style="text-align: center;">
  <iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=dceoy-22&o=9&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=4873116511" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>
</div>
<br>
