---
layout: post
title:  "whenever with capinstrano3"
date:   2016-06-10 00:00:00
categories: whenever gem
blog: true
---

## github
[whenever](https://github.com/javan/whenever)

## rolesまわりに関して

- `whenever_roles`はデフォルトでは`db`が指定してある。
- あるジョブを一部サーバーでのみcrontab設定をするよう制限したい場合は、そのジョブ定義に`:roles => [...]`を引数として渡してあげればよい。ただし`whenever_roles`にそのroleが追加されているようにしなければならない。
- `roles:`引数のないジョブは全サーバーに対して`whenever_roles`に定義された`role`でのデプロイ実行時にcrontab設定される。

## whenever三原則

1. `whenever_roles`にない`role`はcrontab追加をすることはない
    -  @追加することはないどころか、同じサーバーだった場合何もない設定に上書きされてしまう気がする。
2. ある`roleA`が`whenever_roles`にある場合、`roleA`サーバー`crontab`には`roleA`が`:roles`引数に存在するジョブ及び、`:roles`引数が渡されていないジョブが設定される。
3. あるジョブの`:roles`引数が`roleA`であり、`roleA`が`whenever_roles`にない場合はそのジョブはどのサーバーへのデプロイ時であってもcrontab設定されることはない
