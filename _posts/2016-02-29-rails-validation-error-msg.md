---
layout: post
title:  "ActiveRecordデフォルト定義のバリデーションエラーメッセージ名"
date:   2016-02-29 00:00:00
categories: rails validation
blog: true
---

バリデーション時のエラーメッセージの`i18n`で`ja.yml`にデフォルトの`blank`等メッセージの日本語定義をしたかった。
`blank`や`invalid`はすぐ出てくるが、その他の最大文字数制限のエラーメッセージ名がわからなかったので調べた。

詳しくは下記リンクを見ればよい。
[http://guides.rubyonrails.org/i18n.html#error-message-interpolation](http://guides.rubyonrails.org/i18n.html#error-message-interpolation)
