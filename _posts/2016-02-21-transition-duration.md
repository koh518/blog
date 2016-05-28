---
layout: post
title:  "CSS transition-durationが動かない"
date:   2016-02-21 00:00:00
categories: css animation
blog: true
---

## 前提
メニューボタンを押したら、背面に潜んでいる#backが表示されて、#frontが左へスライドするみたいなことをしたい

## 問題
なぜかslide時にanimationが効かない

## 解決策
遷移前表示されている#front()へ``right: 0;``を明記するだけ

## ポイント
遷移前、遷移後の情報を明記しよう

## 上記を踏まえて

![](http://wise-saying.get0ver.net/wp-content/uploads/sites/3/2014/11/Drucker.jpg)

>未来を語る前に、今の現実を知らなければならない。
現実からしかスタートできないからである。
- ピーター・ドラッカー

http://stackoverflow.com/questions/21375518/transition-css-duration-not-working
