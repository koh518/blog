---
layout: post
title:  "【Unix】Argument list too longに負けず、大量ファイルを削除する"
date:   2016-08-12 00:00:00
categories: unix
blog: true
---

## 前提

とあるlogrotateの対象が*になってinode枯渇していることが

{% highlight ruby %}
df -i
{% endhighlight %}

とかしてたら判明した。

普通に頑張ろうと対象ディレクトリ配下に対して

{% highlight ruby %}
rm -rf *
{% endhighlight %}

をするとArgument list too longで怒られて削除できない。

## 解決

{% highlight ruby %}
find . -name ./* | xargs rm -f
{% endhighlight %}


## 参考
http://assimane.blog.so-net.ne.jp/2011-01-15
