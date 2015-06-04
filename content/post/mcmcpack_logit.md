+++
date = "2015-06-03T19:19:34+09:00"
draft = true
title = "MCMC によるロジステック回帰"
tags = ["mcmcpack", "r", "mcmc", "statistics"]

+++

マルコフ連鎖モンテカルロ法 (Markov chain Monte Carlo; MCMC) によるベイズ推定を行うソフトウェアとしては, ギブスサンプラー (Gibbs sampler) の [BUGS (WinBUGS, OpenBUGS)](http://www.mrc-bsu.cam.ac.uk/software/bugs/) や [JAGS](http://mcmc-jags.sourceforge.net/) が有名であり, また近年では, ハミルトニアンモンテカルロ法 (Hamiltonian Monte Carlo; HMC) に基づく [Stan](http://mc-stan.org/) も勢いがある.

BUGS は枯れていて実績があり, Stan は従来の MCMC サンプラーと比較して高速・高効率なサンプリングが可能であるなど, それぞれメリットはあるが, いずれもその言語でモデルを記述する必要があるため, 初学者には多少敷居が高い.

一方, R 上で MCMC を実行する [MCMCpack] (http://mcmcpack.berkeley.edu/) は, インターフェースが R のビルドイン関数に合わせて設計されているため, 少ない事前知識で MCMC を試せる.

MCMCpack
--------

以下は, [MASS](http://cran.r-project.org/web/packages/MASS/index.html) パッケージに含まれる乳癌の生検データから, MCMCpack でロジスティック回帰のパラメーターを推定した例.

<script src="https://gist.github.com/dceoy/3c858d4769cd2991ed71.js?file=mcmc_logit.R"></script>

`MCMClogit()` では, `glm()` と同じような記述でメトロポリス法 (Metropolis algorithm) によるサンプリングを実行できる.  
実装が C++ のため処理も速い.

まとめ
------

R に慣れていれば MCMCpack は簡単に試せる.  
今回は一般化線形モデルの固定効果の例だが, 混合効果モデルに使える関数もある様子.

同様に R 上で MCMC を実行するパッケージとしては他に, [MCMCglmm](http://cran.r-project.org/web/packages/MCMCglmm/index.html) などがある.

ただ, 使えるモデルは限定されるので, 複雑なモデリングや細かいチューニングには BUGS や Stan の方が向いている.

<script>
  amzn_assoc_default_search_key = "マルコフ連鎖モンテカルロ";
</script>
