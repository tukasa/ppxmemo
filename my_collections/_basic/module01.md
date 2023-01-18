---
title: 外部module
part: module
date: 2023-01-16
last_modified_at: 
---

## 正規表現ライブラリ

正規表現によるファイル名の比較や、パターン指定による文字置換を行うために必要となる。

- [K.Takata's Web Page](http://k-takata.o.oo7.jp)からbregonig.dllをダウンロードし、bregonig.dllをPPxフォルダにコピーする。

## migemo

インクリメントサーチでローマ字読み一致検索を行うのに必要になる。
正規表現ライブラリも必要なので、bregonig.dllもインストールしておこう。

- [KaoriYa](https://www.kaoriya.net)からC/Migemo for Windowsをダウンロードし、migemo.dllとdictフォルダをPPxフォルダにコピーする
- カスタマイザーを起動し、「全般タブ - 操作 - インクリメンタルサーチ - ローマ字入力（migemo）を使用する」をチェックする。

![カスタマイザー]({{ "/assets/images/module01.png" | relative_url }})

## Susie Plug-in

SusieプラグインをPPxフォルダに入れると使うことができる。32bit版は.spi、64bit版は.sphとなることにだけ注意。
Susieプラグインがあるディレクトリを指定することもできる。

![カスタマイザー]({{ "/assets/images/module02.png" | relative_url }})
