---
title: PPx Moduleのインストール
part: module
created_at: 2022-03-31
last_modified_at: 2023-07-22
---

[TORO's Software library](http://toro.d.dooo.jp/slppx.html)にあるPPx moduleをインストールすることで、PPxに色々な機能を追加することができる。
インストールは簡単で、ダウンロードした書庫内のPPX○○.DLL（64bit版の場合はPPX○○64.DLL）をPPxフォルダに入れるだけ。例えばWSH Script Module であれば、PPXSCR.DLL（64bit版であればPPXSCR64.DLL）をPPxフォルダにコピーする。

本サイトでは、以下についてはインストールしているものとして扱う。

- Message Module
- Window Module
- Text Module
- WSH Script Module
- Key Module

基本的には、必要なものを必要なときにインストールすればいい。ただ注意が必要なのがEverything Search Moduleだ。これを入れると、一行編集がEverythingの自動補完表示を行い、挙動が遅くなる。 Everything Search Moduleはインストールしたいが、一行編集の自動補完表示はいらないという場合は、以下で抑制する。

```text
K_lied	= {
FIRSTEVENT	,*completelist -module:off
}
```

