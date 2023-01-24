---
title: タイトルを自動更新
part: howm
created_at: 2023-01-24
---

howmファイルを新規作成した際、自動でタイトル表示を更新するようにする。
以下をScriptフォルダに保存する。

_title2comment.js_
<script src="https://gist.github.com/tukasa/52edfb4f0a20435f49541706b8fbe268.js"></script>

howmファイルのあるフォルダで`*diroption -thisbranch cmd:"*script %0Script\title2comment.js %%: *setcust XC_cwrt= 2"`を実行する。これでタイトルを自動更新するようになる。
自動更新を解除したい場合は`*diroption -thisbranch cmd:""`とすればいい。
title2comment.jsはtitle2comment_all.jsと違い、新規ファイルに対してのみ動作する。既存ファイルの一行目を変更し、かつそれをタイトル表示に反映させたい場合は、title2comment_all.jsを使おう。