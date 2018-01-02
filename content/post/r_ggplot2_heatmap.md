+++
date = "2015-05-14T23:52:26+09:00"
title = "ggplot2 で描く heatmap"
tags = ["r", "ggplot2", "visualization"]
+++

heatmap は比較的メジャーな可視化方法なので, 使える R のパッケージも多い.  
ggplot2 でも矩形を敷き詰める `geom_tile` で heatmap のような表現が可能になる.

heatmap using ggplot2
---------------------

以下は描画コードと値のサンプル.

<script src="https://gist.github.com/dceoy/5f3d99084d604b847447.js?file=heatmap.R"></script>
<script src="https://gist.github.com/dceoy/5f3d99084d604b847447.js?file=value.csv"></script>

heatmap は図に対応した値の行列から作図するケースが少なくないと思うが, ggplot2 では上のように, 行列の位置と値をレコードとして持つテーブルから作図する.  
前者はスプレッドシートからの移植性などには優れるものの, 図の列が増えたときにデータが横に広がって処理が煩雑になるが, 後者はその心配がない.

サンプルのデータはシェルからワンライナーで作った.

```sh
$ echo 'row,col,val' > matrix.csv
$ seq -w 0 55 | grep -v '[6-9]' | sed -e 's/\(.\)\(.\)/\1 \2/g' | awk '{ print "row"$1",col"$2","exp(rand() * 10) }' >> matrix.csv
```

下図は出力された SVG.

<div style="text-align: center;">
  <img src="https://rawgit.com/dceoy/5f3d99084d604b847447/raw/plot.svg" alt="plot">
</div>
<br>

まとめ
------

データを位置と値のテーブルとして入力する点が良かった.  
この形式は SQL で抽出したデータを可視化するときなどに有利になる.


<script>
  amzn_assoc_default_search_key = "ggplot2";
</script>
