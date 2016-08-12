---
layout: post
title:  "【Rails】 wicked_pdf 日本語が文字化けする問題"
date:   2016-08-12 00:00:00
categories: rails wicked_pdf
blog: true
---

## 問題
ローカル環境だとうまく動作して検証用EC2へデプロイしてPDF表示したら日本語部分がことごとく文字化けしてしまう。

## 原因

1. EC2にwkhtmltopdfがインストールされていなかった
    - wicked_pdfはwkhtmltopdfをRailsで扱っている感じなので当然ながら必要だった
2. EC2に日本語フォントがインストールされてなかった

## やったこと

### wkhtmltopdfインストール

{% highlight ruby %}
$ mkdir /home/ec2-user/downloads
$ cd /home/ec2-user/downloads
$ sudo wget http://download.gna.org/wkhtmltopdf/0.12/0.12.2.1/wkhtmltox-0.12.2.1_linux-centos6-amd64.rpm
$ sudo yum install -y xorg-x11-fonts-75dpi
$ sudo rpm -ivh wkhtmltox-0.12.2.1_linux-centos6-amd64.rpm
{% endhighlight %}

### 日本語フォントインストール

{% highlight ruby %}
$ cd /usr/share/fonts
$ sudo wget http://download.forest.impress.co.jp/pub/library/i/ipafont/10483/IPAfont00303.zip
$ sudo unzip IPAfont00303.zip
$ fc-cache -fv

# インストールされているか確認
$ fc-list | grep -i ipa
# IPAゴシック,IPAGothic:style=Regular
# IPA Pゴシック,IPAPGothic:style=Regular
# IPA明朝,IPAMincho:style=Regular
# IPA P明朝,IPAPMincho:style=Regular
{% endhighlight %}

## 参考
http://qiita.com/metheglin/items/bb88aa25eae250bfa2a2
http://hacknote.jp/archives/16712/
