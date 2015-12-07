+++
date = "2015-12-08T00:42:15+09:00"
draft = true
title = "SQLite で構築する MedDRA データベース"
tags = ["meddra", "sql", "sqlite", "rdb", "shell", "medicine"]

+++

<div style="text-align: center;">
  <img src="../../images/meddra.png" alt="logo">
</div>
<br>

##### [meddra-sqlite](https://github.com/dceoy/meddra-sqlite)

[ICH 国際医薬用語集 MedDRA](http://www.meddra.org/) の日本版, [MedDRA/J](https://www.pmrj.jp/jmo/php/indexj.php) からリレーショナルデータベースを構築するコード.  
以前書いて GitHub に上げていたものを整理した.

テーブルを定義する SQL とマイグレーションのための bash スクリプトが主体.  
SQLite3 データベースを構築し, ついでにダンプする.

テーブル定義の SQL とダンプした後の SQL は PostgreSQL などでも使えるかも (動作未検証) .


<script>
  amzn_assoc_default_search_key = "meddra";
</script>
