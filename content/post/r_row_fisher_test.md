+++
date = "2015-05-08T00:28:33+09:00"
draft = true
title = "行列の各行で Fisher の正確な検定"
tags = ["r", "statistics"]

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

R で複数の 2 x 2 分割表に対して Fisher の検定で正確な p 値を計算したい, という課題にぶつかったので, 各セルの数値を束ねた行列に対して p 値を算出するコードを書いた.  
stackoverflow にも [似た質問](http://stackoverflow.com/questions/14983579/running-a-fisher-test-on-each-row-of-a-data-frame-in-r) があったので参照のこと.

fisher.test
-----------

2 x 2 分割表 (2 x 2 contingency table) の独立性の検定には, 一般的に x<sup>2</sup> 検定 (Chi-square test) が用いられるが, これは頻度が少なくなると近似が悪くなるので, その場合は正確な p 値を計算する Fisher の正確な検定 (Fisher exact test) を行う方が適している.

R では組み込みの [fisher.test](http://www.inside-r.org/r-doc/stats/fisher.test) で p 値を算出できる.  
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

参考文献
--------

1.  [丹後 俊郎 (1993). 新版 医学への統計学 (統計ライブラリー), 朝倉書店.](http://www.amazon.co.jp/dp/4254125461/ref=as_sl_pc_tf_lc?tag=dceoy-22&camp=1027&creative=7407&linkCode=as4&creativeASIN=4254125461&adid=0EGQ4BEFAAWWB3GKNYP5&&ref-refURL=http%3A%2F%2Frcm-fe.amazon-adsystem.com%2Fe%2Fcm%3Flt1%3D_blank%26bc1%3D000000%26IS2%3D1%26bg1%3DFFFFFF%26fc1%3D000000%26lc1%3D0000FF%26t%3Ddceoy-22%26o%3D9%26p%3D8%26l%3Das4%26m%3Damazon%26f%3Difr%26ref%3Dss_til%26asins%3D4254125461)


<script>
  amzn_assoc_default_search_key = "r programming";
</script>
