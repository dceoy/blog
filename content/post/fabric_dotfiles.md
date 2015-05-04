+++
date = "2015-05-05T02:48:32+09:00"
draft = true
title = "Fabric による開発環境の管理"
tags = ["Fabric", "Python", "Vim", "Zsh", "Linux", "Mac"]

+++

[dceoy/dotfiles](https://github.com/dceoy/dotfiles)

dotfiles
--------

Linux や Mac を使うエンジニアが . から始まる設定ファイルをクラウドで管理することがあると思う.  
私も Zsh や Vim を使うので .zshrc や .vimrc を GitHub に置いている.  
新しい環境でも dotfiles を clone してシンボリックリンクを貼れば, すぐに自分の環境で操作ができるので, 非常に便利.

... と, 初めはそれだけだったが, 次第にシェルやエディタ以外の環境も同じようにしたいと考え始め, そのためのスクリプトもリポジトリに置くようになった.  
現在はそれを [Fabric](http://www.fabfile.org/) に集約し, プロビジョニングのインターフェースを整えている.

Fabric
------

サーバーのプロビジョニングというば [Chef](https://www.chef.io/chef/) や [Puppet](https://puppetlabs.com/) が有名で, 最近では [Ansible](http://www.ansible.com/) も人気がある.  
Fabric も同様, プロビジョニングの自動化に使えるが, 上記のものより小さくシンプルで, SSH 経由でシェルコマンドを実行するツールである, と私は理解している.  
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

私の書いたコマンドについては [README](https://github.com/dceoy/dotfiles) に記載している.  
設定やパッケージはリポジトリ内の `config.yml` で管理するようにした.

特に用途で環境を分けていないので, `rhel_env` と `osx_env` のコマンドは全部盛り.  
例えば `rhel_env` は, この記事を書いた時点で, 以下を自動化している.

- yum でパッケージをインストール
- シェルを Zsh へ変更
- dotfiles を設置
- Python, Ruby, Node.js のバージョン管理ツールを導入
- Vim のプラグイン管理ツールを導入
- Python, Ruby, Node.js, Go, R のパッケージをインストール
- Vim のプラグインをインストール

これらがコマンド 1 つで済むので, 環境構築はかなり省力化できた.  
また, 簡易的ではあるが冪等性も考慮しているので, 一度作った環境にも適用できる.

まとめ
------

Fabric は学習コストが小さい割に強力な自動化ツールとなる.  
シェルスクリプトを書けるのであれば, Python を書いたことがない人でも比較的容易に使えると思われる.  
Python のランタイムは Linux や Mac なら最初からあるので, 是非試していただきたい.

このリポジトリに関しては飽くまで個人使用のために作っているので, 参考にされる方は各々に適した設定で書いていただければと思う.

<div style="text-align: center;">
  <iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=hue-22&o=9&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=4873113938" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>
</div>
<br>
