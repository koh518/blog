---
layout: post
title:  "Ruby return and next in loop"
date:   2016-04-09 00:00:00
categories: Ruby
blog: true
---

## ループ内でのnextとreturn

### next
次のループ処理へ進む

### return
そのメソッド自体を抜ける。

{% highlight ruby %}
# 偶数のみ標準出力する
numbers.each do |n|
  next if (n % 2) == 1
  puts n
end
{% endhighlight %}
