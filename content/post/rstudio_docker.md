+++
date = "2015-12-09T23:28:45+09:00"
draft = true
title = "RStudio Server on Docker"
tags = ["docker", "fabric", "ubuntu", "digitalocean", "r", "rstudio_server"]

+++

<div style="text-align: center;">
  <img src="../../images/rstudio.png" alt="logo">
</div>
<br>

##### [dceoy/rstudio-server-docker](https://github.com/dceoy/rstudio-server-docker)

[RStudio Server](https://www.rstudio.com/products/rstudio/) の Dockerfile を作った.  
Ubuntu のベースイメージからで latest の RStudio Server をインストールして起動する.

ビルドしたイメージは [Docker Hub](https://hub.docker.com/) からも利用可能.

```sh
$ docker pull dceoy/rstudio
```

ついでに Fabric を使ってこのイメージをデプロイするツールも作った.  
とりあえず [DigitalOcean](https://www.digitalocean.com/?refcode=2b30b7b68ac5) へのデプロイを想定したが, 他のサーバーでも使用可能.

##### [dceoy/fab-rstudio-docker](https://github.com/dceoy/fab-rstudio-docker)

(実のところ, 私自身は R を Vim で書いて Shell から実行することが多いので, これを使う機会があまりない.)


<script>
  amzn_assoc_default_search_key = "RStudio";
</script>
