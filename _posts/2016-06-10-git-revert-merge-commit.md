---
layout: post
title:  "【git】MergeコミットをRevertする"
date:   2016-06-10 00:00:01
categories: git revert
blog: true
---

`git revert -m 1 hashashahshashhahshshshsh`

- `-m`は`--mainline`の省略形。
    - `1`: mergeされたブランチをmaillineとする
    - `2`: mergeしたブランチをmaillineとする

`-m 1`が必要になるケースが圧倒的に多い気がするがどうだろう。

参考
http://d.hatena.ne.jp/koba04/20121122/1353512656
