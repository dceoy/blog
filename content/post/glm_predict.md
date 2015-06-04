+++
date = "2015-05-22T19:02:44+09:00"
draft = true
title = "ロジスティック回帰に基づく予測と可視化"
tags = ["glm", "r", "predict", "ggplot2", "statistics"]

+++

[UCLA のページ](https://idre.ucla.edu/)の[ロジスティック回帰の例](http://www.ats.ucla.edu/stat/r/dae/logit.htm)に [predict](http://www.inside-r.org/r-doc/stats/predict) で出力した予測確率のグラフがあったので, これを参考に[前回の記事](/post/glm_confint/)のモデルで可視化してみた.

今回のモデルは 2 つの説明変数を持つため, `glucose` の値を四分位点毎に固定し, `diabetes` を横軸, 予測確率を縦軸に取って作図した.  
信頼区間は標準誤差から計算している.

<script src="https://gist.github.com/dceoy/b33beb466680808f3d6e.js?file=glm_predict.R"></script>

下図は出力された SVG.

<div style="text-align: center;">
  <img src="https://rawgit.com/dceoy/b33beb466680808f3d6e/raw/plot.svg" alt="plot">
</div>
<br>

glm オブジェクトに適用する `predict()` の実体は [predict.glm](http://www.inside-r.org/r-doc/stats/predict.glm) となる.  
モデルによって扱い方が異なる関数なので, 調べるときは注意が必要.

今回は信頼区間の計算も自前でしているが, lm オブジェクトを引数に取る [predict.lm](http://www.inside-r.org/r-doc/stats/predict.lm) などには信頼区間や予測区間を出すオプションがある. (predict.glm にはないらしい.)


<script>
  amzn_assoc_default_search_key = "ロジスティック回帰";
</script>
