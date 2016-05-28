---
layout: post
title:  "Capistrano 意図しないRole処理が実行されてしまう問題"
date:   2016-03-15 00:00:00
categories: linux oom
blog: true
---

## 前提

{% highlight ruby %}
require 'net/ssh/proxy/command'

# bin/cap --roles=web some_env deploy

role :web, %w{xx.xxx.xxx.xxx}
role :app, %w{xx.xxx.xxx.xxx}
role :db, %w{xx.xxx.xxx.xxx}

set :ssh_options, {
  user: 'some-user',
  keys: [File.expand_path('~/.ssh/id_rsa')],
  auth_methods: %w(publickey)
}

on roles(:app) do
  set :deploy_to, "/home/some-user/#{fetch(:application)}"
end

on roles(:web) do
  set :deploy_to, "/var/www/#{fetch(:application)}"
end
{% endhighlight %}

上記のような`config/deploy/some_env.rb`を書いて

{% highlight ruby %}
bin/cap --roles=web some_env deploy
{% endhighlight %}

を実行した場合に`rake db:migration`が走ったり、

`--roles=app`なのに`/var/www/app/`配下へデプロイしてしまう問題に直面した。

##  原因

***どうやらIPが同じ場合にはcapistranoがそのIPに設定されているroleを全て実行してしまうようだった***
(書き方が悪い説はある。)

その為今回はdeploy時に実行したくないroleがある場合はコメントアウトすることにした。(イケてない)

確認用環境だし、そもそもサーバーが別々でないならpathを別にきる必要とかもない気がするので今回はまぁよしとすることにした。
