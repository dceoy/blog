+++
date = "2015-05-21T05:12:28+09:00"
draft = true
title = "R でのロジスティック回帰と係数の信頼区間"
tags = ["glm", "r", "statistics"]

+++

\[
  \ln(\frac{ p }{ 1 - p })  = \alpha + \beta_1 x_1 + \beta_2 x_2
\]

R でのロジスティック回帰には, 一般化線形モデル (Generalized Linear Model; GLM) を扱う [glm](http://www.inside-r.org/r-doc/stats/glm) をよく使うが, この返り値に [confint](http://www.inside-r.org/r-doc/stats/confint) を当てれば回帰係数の信頼区間 (Confidence Interval; CI) を算出できる.

今回は, パッケージ [faraway](http://cran.r-project.org/web/packages/faraway/index.html) で得られるピマインディアンの糖尿病検査のデータ `pima` を例に, ロジスティック回帰を行い, 係数の信頼区間を計算した.

<script src="https://gist.github.com/dceoy/b33beb466680808f3d6e.js?file=glm_confint.R"></script>

オッズ比は回帰係数で `exp()` を取れば算出される.


<script>
  amzn_assoc_default_search_key = "一般化線形モデル";
</script>
