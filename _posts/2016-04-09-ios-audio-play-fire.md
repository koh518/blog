---
layout: post
title:  "iOS Safari audio.play()が発火しない問題"
date:   2016-04-09 00:00:00
categories: iOS Safari JavaScript
blog: true
---

## 原因調査

### [iOS/Android で HTML5 の audio/video を任意のタイミングで再生する方法](http://dsuket.hatenablog.com/entry/2013/05/05/101430)

> iOS の Safari では、ユーザーが携帯網で重量課金されるかもしれないから、preload と autoplay は効かないよ。ユーザーが何かアクションしないと、JavaScript での play() や load() もダメ。つまり、再生ボタンを押して play() を呼べるけど、onload で play() しても無効だから。

### [iOS-Specific Considerations](https://developer.apple.com/library/safari/documentation/AudioVideo/Conceptual/Using_HTML5_Audio_Video/Device-SpecificConsiderations/Device-SpecificConsiderations.html)

> In Safari on iOS (for all devices, including iPad), where the user may be on a cellular network and be charged per data unit, preload and autoplay are disabled. No data is loaded until the user initiates it. This means the JavaScript play() and load() methods are also inactive until the user initiates playback, unless the play() or load() method is triggered by user action. In other words, a user-initiated Play button works, but an onLoad="play()" event does not.


## 対応

サイト内でユーザーアクションの後で`audio.play()`するようにした。
