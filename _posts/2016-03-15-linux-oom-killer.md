---
layout: post
title:  "Unicorn起動タイミングでCapistranoがコケる"
date:   2016-03-15 00:00:00
categories: linux oom
blog: true
---

結論から言うとメモリ不足。EC2インスタンスが予想外に弱かった(t2.micro)


Linux上でのKillログは

{% highlight bash %}
cat /var/log/messages | grep Killed
{% endhighlight %}

とかすると見れる。`tail -f /var/log/messages`とかしてデプロイしたら

{% highlight bash %}
Out of memory: Kill process 14667 (ruby) score 114 or sacrifice child
Killed process 14700 (ruby) total-vm:457252kB, anon-rss:116156kB, file-rss:24kB
{% endhighlight %}

とかが見れる。


[http://qiita.com/konpyu/items/20d1989d1251d805cf3b](http://qiita.com/konpyu/items/20d1989d1251d805cf3b)
