+++
date = "2015-05-21T05:12:28+09:00"
draft = true
title = "[R] ロジスティック回帰と係数の信頼区間"
tags = ["glm", "confint", "r", "faraway", "statistics"]

+++

[R でのロジスティック回帰](http://www.ats.ucla.edu/stat/r/dae/logit.htm)には, 一般化線形モデル (Generalized Linear Model; GLM) を扱う [glm](http://www.inside-r.org/r-doc/stats/glm) をよく使うが, この返り値に [confint](http://www.inside-r.org/r-doc/stats/confint) を当てれば回帰係数の信頼区間 (Confidence Interval; CI) を算出できる.

以下では, パッケージ [faraway](http://cran.r-project.org/web/packages/faraway/index.html) で得られるピマインディアンの糖尿病検査のデータ `pima` を例に, ロジスティック回帰を行い, 係数の信頼区間を計算した.

<script src="https://gist.github.com/dceoy/b33beb466680808f3d6e.js?file=glm_ci.R"></script>

オッズ比は回帰係数で `exp()` を取れば算出される.

<div style="text-align: center;">
  <iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=dceoy-22&o=9&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=4873115337" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>
</div>
<br>
