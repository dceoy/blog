+++
date = "2015-05-06T01:22:33+09:00"
draft = true
title = "[R] スクリプト内でパッケージをインストールする"
tags = ["R"]

+++

R のコンソールから対話式で CRAN ミラーを選び, パッケージをインストールするのは面倒だと思う.  
以下のように書けば R スクリプト内で処理が完結する.

<script src="https://gist.github.com/dceoy/c472e300cd0423023869.js?file=cran_pkg_load.R"></script>

スクリプトの上流に貼れば, ローカルにないパッケージがあっても, インストール, アップデート, ロードを自動でやってくれるので, 手間が減る.

<div style="text-align: center;">
  <iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=dceoy-22&o=9&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=4873116511" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>
</div>
<br>
