---
layout: post
title:  "Rails ActionMailerに自前のdelivery methodを設定する方法"
date:   2016-02-21 00:00:00
categories: css animation
blog: true
---

Action Mailer delivery method image
![](http://image.itmedia.co.jp/nl/articles/1312/02/kuro_131202primeair01.jpg)

## 初トライ
愚直に`config.action_mailer.delivery_method = :smtp`を参考にして

`config.action_mailer.delivery_method = :my_delivery_method_class`としてdeliver!してみる
=> `RuntimeError: Invalid delivery method :my_delivery_method_class`

アカンかった

## 問題

[http://api.rubyonrails.org/classes/ActionMailer/Base.html](http://api.rubyonrails.org/classes/ActionMailer/Base.html)によると

{% highlight ruby %}
delivery_method - Defines a delivery method. Possible values are :smtp (default), :sendmail, :test, and :file.

Or you may provide a custom delivery method object e.g. MyOwnDeliveryMethodClass.
# せやなかったら、たとえばMyOwnDeliveryMethodClassみてーな、アンタのつくうたカスタムdelivery methodオブジェクトを設定できるで
{% endhighlight %}

## 旅立ち

`config.action_mailer.delivery_method = MyOwnDeliveryMethodClass`
