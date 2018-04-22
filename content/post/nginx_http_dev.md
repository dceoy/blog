---
date: 2015-12-12T22:48:57+09:00
title: "HTTP サーバーでユーザーのディレクトリを公開する"
tags: ["nginx", "http", "fedora", "linux", "python", "web"]
---

<div style="text-align: center;">
  <img src="../../images/nginx.png" alt="logo">
</div>
<br>

VirtualBox や VMware を使ってローカルのマシンに Linux の環境を作り, データ分析やソフトウェア開発をする際, ホストのブラウザからコンテンツを見たくなることがある.

Python 組み込みの HTTP サーバーを使えば, これは簡単に実現する.

Python HTTP Server
------------------

Python 2

```sh
$ python -m SimpleHTTPServer
```

Python 3

```sh
$ python -m http.server
```

これは Web 系でなくても使えるテクニックで, 例えば, データ分析で出てきた結果の画像ファイルを見たりするのに使える.

しかし, 毎回コマンドを実行するのは面倒だし, Python のサーバーは遅い.  
それが気になる場合は, デーモンで HTTP サーバーを実行し, ホーム下のディレクトリを公開すればいい.

自分はこの用途で [Nginx](http://nginx.org/) を使っている.

Nginx
-----

軽量で高速, 高機能な HTTP サーバー.  
Web サーバーといえば [Apache](https://httpd.apache.org/) のシェアが大きいが, 近年は Nginx もよく使われる.

以下は Nginx を開発環境で使うまでの手順の例.

1.  Nginx をインストール
2.  SELinux を設定する, もしくは切る
3.  Firewall で HTTP を許可する, もしくは切る
4.  公開ディレクトリのパーミッションを設定
5.  Nginx のドキュメントルートに公開ディレクトリのシンボリックリンクを貼る
6.  ディレクトリ一覧を見えるようにする (`nginx.conf` で `autoindex on`)
7.  Nginx を起動

自分はホームディレクトリを公開してその下のファイルを全て見えるようにしている.  
[環境管理用の Fabric のコード](https://github.com/dceoy/fabkit)にもタスクを追加した.

使った感想としては, 軽くて速い.

まとめ
------

デーモンから Nginx を起動してユーザーのディレクトリを公開すれば, 都度サーバーを立ち上げる手間を省ける.  
加えて, Nginx は速い.

このくらいの用途なら細かく設定する必要もないので, データ分析などにも使い易いと思う.

---

2016-07-03 追記:

- [Docker image](https://github.com/dceoy/docker-nginx-autoindex) を作った.


<script>
  amzn_assoc_default_search_key = "nginx";
</script>
