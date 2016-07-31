---
layout: post
title:  "【AR】 Vuforia + Unity マーカー発見時に動画再生をする"
date:   2016-07-31 00:00:00
categories: ruby rails i18n active_model
blog: true
---

## はじまり
pokemon goが世界的に人気があり、AR技術に興味があったので色々ググッてみて簡単なものをつくってみた。

## つくったもの

<img src="/assets/images/giftee.jpg" style="width:50%;border: 1px #f2f2f2 solid;" />
<img src="/assets/images/giftee_5anniv_logo.png" style="width:48%;border: 1px #f2f2f2 solid;" />

上記２つの画像をマーカーとして設定して、アプリケーションがそれを見つけた場合に関連する動画がみれるというもの。

## 今回説明を省略していること
- Vuforia会員登録
- Unity会員登録

## Vuforia License + Target

[https://developer.vuforia.com/](https://developer.vuforia.com/)から行う

このあたりは[Unityでも使える無料ARライブラリVuforiaの基礎知識とライセンス登録、インストール、簡単な使い方](http://www.atmarkit.co.jp/ait/articles/1508/24/news025_2.html)がうまくまとめてくれている。

## Unity with Vuforia

このあたりは[Unity + Vuforia でARな動画再生を試してみた](http://qiita.com/JunSuzukiJapan/items/f6ed23bb519d01fdaaa3)がわかりやすかった。

#### ArCamera設定

上記記事内【ARCameraの設定】のなかに`VideoPlaybackController`をARCameraに設定する部分がある。
2016-07-31現在では[Samples](https://developer.vuforia.com/downloads/samples)からAdvanced TopicsのUnity向けのpackageを持ってきてもそんなものはなかった。
結果として動画再生がうまく行われない問題にハマった。

解決策としては、`ARCamera`へ

{% highlight ruby %}
VideoPlaybackTapHandler
PlayVideo
VideoPlaybackMenuOptions
{% endhighlight %}


をScriptとして追加した。

## できたもの

<img src="/assets/images/2016-07-31/5anniv_demo.jpeg" style="width:50%;border: 1px #f2f2f2 solid;" />
<img src="/assets/images/2016-07-31/welcome_giftee_demo.jpeg" style="width:48%;border: 1px #f2f2f2 solid;" />






## 参考

- [Unityでも使える無料ARライブラリVuforiaの基礎知識とライセンス登録、インストール、簡単な使い方 (1/3)](http://www.atmarkit.co.jp/ait/articles/1508/24/news025.html)
- [Vuforiaで立体をARマーカーにしてスケスケ＆動画再生 (1/4)](http://www.atmarkit.co.jp/ait/articles/1601/08/news034.html)
- [【３０分でできる】Unityで簡単にARアプリを作る](http://makers.hatenablog.com/entry/2013/12/27/191636)
- [Unity + Vuforia でARな動画再生を試してみた](http://qiita.com/JunSuzukiJapan/items/f6ed23bb519d01fdaaa3)
