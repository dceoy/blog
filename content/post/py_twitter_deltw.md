+++
date = "2015-05-19T22:16:50+09:00"
draft = true
title = "Twitter API から取得できない古いツイートを削除する"
tags = ["python", "twitter", "api"]

+++

<div style="text-align: center;">
  <img src="../../images/twitter.png" alt="logo">
</div>
<br>

##### [del-tw](https://github.com/dceoy/del-tw)

Twitter API のユーザータイムライン取得は, [最新の 3,200 ツイート](https://dev.twitter.com/rest/reference/get/statuses/user_timeline)までに限られる.  
このため, API 経由でツイートを削除するサービスは 3,200 より古いツイートを削除できない.

これを解決すべく, 古いツイートも削除するコードを書いた.

具体的には, 以下の手順で行う.

> 1. Twitter から Archive (全ツイート履歴) をダウンロード
> 2. Archive から過去のツイートの Status ID を抽出
> 3. OAuth 認証後, Status ID で REST API を叩き, ツイートを削除

[README](https://github.com/dceoy/del-tw) に書いたプロセスも上記に従うが, こちらはアーカイブされたツイートを全て削除するので, 取捨選択する場合には適宜対応する.

Your Twitter Archive
--------------------

Twitter では[自分のツイートのアーカイブ](https://support.twitter.com/articles/20170160-downloading-your-twitter-archive)が zip ファイルで提供される.  
中身は HTML や JavaScript で, `index.html` を開いてツイートをブラウズする.

ここで個々のツイートのリンクを開けば URL から Status ID を確認可能.  
以下の例では末尾の数字が ID.

    https://twitter.com/dceoy/status/599953191317311488

ツイートの情報は `data/js/tweets/` 以下に JavaScript として保存されているので, 今回は ID 抽出前にこれらを 1 つの JSON にまとめた.  
集約は Sed で済む.

```sh
$ sed -e 's/^Grailbird.*$/\[/' archive/data/js/tweets/*.js \
    | sed -e 's/Grailbird.*$/,/g' > data/tweets.json
$ echo ']' >> data/tweets.json
```

出力される JSON は年月単位, ツイート単位の階層を持ち, `id_str` をキーに ID を抽出できる.  
以降は Python で書いた.

Requests-OAuthlib
-----------------

操作に認証が必要なので, OAuth のライブラリとして [Requests-OAuthlib](https://github.com/requests/requests-oauthlib) を使った.  
認証後は [REST API](https://dev.twitter.com/rest/public) を叩く.

[POST statuses/destroy/:id](https://dev.twitter.com/rest/reference/post/statuses/destroy/%3Aid)

今回書いた `delete_tw.py` は, 先述の階層を持つ JSON を引数として渡すと, ID 毎に上の HTTP リクエストを発行し, 該当ツイートを削除する.

まとめ
------

コンパクトに収まったと思う.  
Twitter の REST APIs は流石によくできていて利用しやすい.

---

2016-02-29 追記:

- [コードを Python に集約](https://github.com/dceoy/del-tw). ZIP を引数に JSON を生成せず実行する.


<script>
  amzn_assoc_default_search_key = "twitter api";
</script>
