+++
date = "2015-05-06T01:22:33+09:00"
draft = true
title = "[R] スクリプトでパッケージをインストール"
tags = ["r"]

+++

R のコンソールから CRAN ミラーを選んでパッケージをインストールするのは面倒なので, 以下のように書いてスクリプトの中で処理している.

<script src="https://gist.github.com/dceoy/c472e300cd0423023869.js?file=cran_pkg_load.R"></script>

スクリプトの上流に貼れば, ローカルにないパッケージがあっても, インストール, アップデート, ロードを自動でやってくれるので, 手間が減る.


<script>
  amzn_assoc_default_search_key = "r programming";
</script>
