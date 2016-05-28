---
layout: post
title:  "【正規表現】Rails 半角カナ判定バリデーション【Validation】"
date:   2016-02-25 00:00:00
categories: ruby rails regexp
published: true
---

半角カナがあったらエラーを出してあげて、問題になっている半角カナを出力するバリデーションを書いた。
Fat Modelにならないように、validation実装をmoduleに切り出してみた。

{% gist 67fbf17a2619faea497a %}

[http://konbu13.hatenablog.com/entry/2014/03/03/072330](http://konbu13.hatenablog.com/entry/2014/03/03/072330)
[http://blog.livedoor.jp/skky2/archives/937200.html](http://blog.livedoor.jp/skky2/archives/937200.html)
