---
layout: post
title:  "iOS device登録がいつまでもloadingで終わらない"
date:   2016-02-20 21:34:25
categories: normal
blog: true
---

## 問題
chromeでdevice登録がいつまでも終わらず困った


## 解決法

コンソールを開いたら

{% highlight swift %}
Uncaught jquery.cookie.js?${info.entry.commit.revision}:25 Uncaught
URIError: URI malformed
{% endhighlight %}

とログが出ていた

safariを使って同じ作業を実行したらうまくいった。

##  結論
safariを使おう
