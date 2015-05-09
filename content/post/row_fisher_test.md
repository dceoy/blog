+++
date = "2015-05-08T00:28:33+09:00"
draft = true
title = "[R] 行列の各行で Fisher の正確な検定"
tags = ["r", "fisher.test", "data.table", "dplyr", "snow", "statistics"]

+++

<style>#ct td { text-align: center; }</style>
<table id="ct" align="center">
  <tbody>
    <tr>
      <td></td>
      <td>outcome 1</td>
      <td>outcome 2</td>
    </tr>
    <tr>
      <td>group 1</td>
      <td>a</td>
      <td>b</td>
    </tr>
    <tr>
      <td>group 2</td>
      <td>c</td>
      <td>d</td>
    </tr>
  </tbody>
</table>

複数の 2 x 2 分割表に対して Fisher の検定で正確な p 値を計算したい, という課題にぶつかったので, 各セルの数値を束ねた行列に対して p 値を算出するコードを書いた.  
stackoverflow にも [似た質問](http://stackoverflow.com/questions/14983579/running-a-fisher-test-on-each-row-of-a-data-frame-in-r) があったので参照のこと.

fisher.test
-----------

2 x 2 分割表 (2 x 2 contingency table) の独立性の検定には, 一般的に x<sup>2</sup> 検定 (Chi-square test) が用いられるが, これは頻度が少なくなると近似が悪くなるので, その場合は正確な p 値を計算する Fisher の正確な検定 (Fisher exact test) を行う方が適している.

R では組み込みの [fisher.test](https://stat.ethz.ch/R-manual/R-patched/library/stats/html/fisher.test.html) で p 値を算出できる.  
この関数はオッズ比と信頼区間も出力するが, こちらは[計算方法が異なる](http://oku.edu.mie-u.ac.jp/~okumura/stat/fishertest.html)ので注意が必要.

こうした正確な検定は計算量が多いため, 処理に時間がかかる.

Fisher test on each row of data table
-------------------------------------

普段使う [dplyr](https://github.com/hadley/dplyr) と [data.table](https://github.com/Rdatatable/data.table) に加え, [snow](http://cran.r-project.org/web/packages/snow/) での並列化を前提とした.

下記のコードは, 分割表のセルの数値を束ねた data.table の各行に fisher.test を実行し, p 値, オッズ比と信頼区間を含めた data.table を返す.

<script src="https://gist.github.com/dceoy/4d75564e5f44702ee3bc.js?file=row_fisher_dt.R"></script>

parallel は `detectCores()` に使った.

下記は dplyr, data.table, snow を使わないコード.  
並列化はしていない. `row_fisher` は上と同じ関数.

<script src="https://gist.github.com/dceoy/4d75564e5f44702ee3bc.js?file=row_fisher_df.R"></script>

まとめ
------

R では for ループを使いたくないので apply のファミリーで何とかする.  
snow で並列化もしているのでそこそこ速い.

Fisher の検定など分割表については以下の書籍が参考になった.

<div style="text-align: center;">
  <iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=dceoy-22&o=9&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=4254125461" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>
</div>
<br>
