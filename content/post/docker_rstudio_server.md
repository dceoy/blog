---
date: 2015-12-09T23:28:45+09:00
title: "RStudio Server on Docker"
tags: ["docker", "r", "rstudio_server", "ubuntu", "fabric", "digitalocean"]
---

<div style="text-align: center;">
  <img src="../../images/rstudio.png" alt="logo">
</div>
<br>

##### [dceoy/rstudio-server-docker](https://github.com/dceoy/rstudio-server-docker)

[RStudio Server](https://www.rstudio.com/products/rstudio/) の Dockerfile を作った.  
Ubuntu のベースイメージからで latest の RStudio Server をインストールして起動する.

ビルドしたイメージは [Docker Hub](https://hub.docker.com/r/dceoy/rstudio-server/) からも利用可能.

```sh
$ docker pull dceoy/rstudio-server
```

ついでに Fabric でイメージをデプロイするコードを書いた.  
とりあえず [DigitalOcean](https://www.digitalocean.com/?refcode=2b30b7b68ac5) を想定したが, 他のサーバーでも使用可.

##### [dceoy/fab-rstudio-docker](https://github.com/dceoy/fab-rstudio-docker)

---

2016-07-03 追記:

- リポジトリ名を GitHub で `rstudio-server-docker` から `docker-rstudio-server` に, Docker Hub で `rstudio` から `rstudio-server` に変更.


<script>
  amzn_assoc_default_search_key = "RStudio";
</script>
