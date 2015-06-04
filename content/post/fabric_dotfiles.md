+++
date = "2015-05-05T02:48:32+09:00"
draft = true
title = "Fabric による開発環境の管理"
tags = ["fabric", "python", "vim", "zsh", "linux", "mac"]

+++

##### [dceoy/dotfiles](https://github.com/dceoy/dotfiles)

Linux や Mac を使うエンジニアが "." から始まる設定ファイルをクラウドで管理することはあると思う.  
自分も Zsh や Vim を使うので `.zshrc` や `.vimrc` などを GitHub に置いている.  
新しい環境でも dotfiles を clone してシンボリックリンクを貼れば, すぐに使い慣れたシェルやエディターを使えて便利.

... と, 初めはそれだけだったが, 次第にシェルやエディタ以外の環境も同じようにしたいと考え始め, そのためのスクリプトもリポジトリに置くようになった.  
現在はそれを [Fabric](http://www.fabfile.org/) に集約し, プロビジョニングのインターフェースを整えている.

Fabric
------

サーバーのプロビジョニングというば [Chef](https://www.chef.io/chef/) や [Puppet](https://puppetlabs.com/) が有名で, 最近では [Ansible](http://www.ansible.com/) も人気がある.  
Fabric も同様, プロビジョニングの自動化に使えるが, 上記のものより小さくシンプルで, SSH 経由でシェルコマンドを実行するツールである, と自分は理解している.  
そのシンプルさ故, 学習コストが小さくて済むのが特徴.

Fabric は Python で書かれており, pip や easy_install からインストールできる.  
現時点では Python 3 に対応していない.

```sh
$ pip install fabric
```

タスクの実行は以下の通り.

```sh
$ fab [options] <command>[:arg1,arg2=val2,host=foo,hosts='h1;h2',...]
```

開発環境構築の自動化
--------------------

書いたコマンドについては [README](https://github.com/dceoy/dotfiles) に記載している.  
設定やパッケージはリポジトリ内の `config.yml` で管理するようにした.

特に用途で環境を分けていないので, `rhel_env` と `osx_env` のコマンドは全部盛り.  
例えば `rhel_env` は, この記事を書いた時点で, 以下を自動化している.

> - yum でパッケージをインストール
> - シェルを Zsh へ変更
> - dotfiles を設置
> - Python, Ruby, Node.js のバージョン管理ツールを導入
> - Vim のプラグイン管理ツールを導入
> - Python, Ruby, Node.js, Go, R のパッケージをインストール
> - Vim のプラグインをインストール

これらがコマンド 1 つで済むので, 環境構築はかなり省力化できた.  
また, 簡易的ではあるが冪等性も考慮しているので, 一度作った環境にも適用できる.

まとめ
------

Fabric は学習コストが小さい割に強力な自動化ツールとなる.  
シェルスクリプトを書けるのであれば, Python を書いた経験のない人でも難しくはないだろうし, Python のランタイムは Linux や Mac なら最初からあるので, 試しやすいと思う.


<script>
  amzn_assoc_default_search_key = "linux";
</script>
