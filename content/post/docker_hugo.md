---
title: "Hugo on Docker"
date: 2018-04-22T10:58:37Z
tags: ["docker", "docker-compose", "hugo", "github"]
---

<div style="text-align: center;">
  <img src="../../images/hugo.png" alt="logo">
</div>
<br>

2 年半近くブログ記事を書いていなかったが, その間に作ったものも GitHub に溜まってきたので, それをネタに少し記事を書いていくことにした.
今回は [Docker](https://www.docker.com/) を使った Hugo ベースのブログ運用について.

Blog powered by Hugo
--------------------

[過去の記事](/post/hugo_blog.md)に書いたように, このブログは [Hugo](https://gohugo.io/) を使って生成しているが, それでもあまりにブログを書いていないので使い方を忘れてしまうという (些末な) 課題が生じた.

しかし, それで毎回ググっていたのでは手間なので, 面倒な作業は [Docker Compose](https://docs.docker.com/compose/) で行うようにした.

Docker image for Hugo
---------------------

まずは Hugo の Docker image を作った.

- Docker image (Docker Hub): [dceoy/hugo](https://hub.docker.com/r/dceoy/hugo/)

- Dockerfile (GitHub): [dceoy/docker-hugo](https://github.com/dceoy/docker-hugo)

Hugo with Docker Compose
------------------------

このブログのビルド & デプロイは [Wercker](http://www.wercker.com/) と [GitHub Pages](https://pages.github.com/) で自動化してあるので, 自分で使うコマンドは `hugo new` (記事生成) と `hugo server` (web サーバー起動) くらいである.
さらに, `hugo new` は大抵オプションを指定せずに使うので, 面倒なのは `hugo server` だけ.

そこで [`docker-compose.yml`](https://github.com/dceoy/blog/blob/master/docker-compose.yml) に Web サーバーの設定を書いてブログの repository に追加した.

- `--theme=nofancy`
  - 使っているテーマを指定する. このブログでは [nofancy](https://github.com/dceoy/nofancy).
- `user: \${UID}:${GID}`
  - 出力ファイルを ownership を制御するため, `UID="\$(id -u)" GID="\$(id -g)"` のように環境変数をセットしておく.
    (デフォルト設定の場合, Docker コンテナから出力したファイルの ownership は root に付くため)
  - Docker for Mac では不要.

<script src="https://gist.github.com/dceoy/fe729a18f603b0875e6ae66498b7bd06.js"></script>

以下のようにコンテナを起動すれば, Web サーバーが `http://127.0.0.1:1313/blog/` で立ち上がる.

```sh
$ docker-compose up
```

これでブログを書くのが少し楽になった.


<script>
  amzn_assoc_default_search_key = "docker";
</script>
