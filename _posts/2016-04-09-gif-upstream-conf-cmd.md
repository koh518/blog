---
layout: post
title:  "【Git】 ローカルブランチをリモートトラッキングブランチに関連付ける"
date:   2016-04-09 00:00:00
categories: git
blog: true
---

### 1. ローカルdevelopブランチをorigin/developに関連付ける

{% highlight bash %}
git branch -u origin/develop develop
{% endhighlight %}

### 2. 引数なしで呼べる

{% highlight bash %}
git pull
{% endhighlight %}
