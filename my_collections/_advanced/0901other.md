---
title: 2画面
part: その他
created_at: 2023-01-13
last_modified_at: 2023-08-19
---

PPxを2画面にする。

![2画面]({{ "/assets/images/2window01.png" | relative_url }})

２画面にするには

- SETUP.EXEでの初期カスタマイズ
- メニューバー - View - ウィンドウ - 窓オプション
- カスタマイザの全般 - PPc - 画面構成
- CFGファイルの取込

といった方法がある。「SETUP.EXEでの初期カスタマイズ」以外はPPxの再起動が必要。

## SETUP.EXEの初期設定

SETUP.EXEを実行して「次へ」をクリックしていくと、途中で設定箇所がある。

![setup]({{ "/assets/images/2window02.png" | relative_url }})

## 窓オプション

「メニューバー - View - ウィンドウ - 窓オプション」で一体化をチェックする。

![窓オプション]({{ "/assets/images/2window03.png" | relative_url }})

## カスタマイザの全般

「カスタマイザの全般 - PPc - 画面構成」で「複数PPcを一体化させ、1ウィンドウにする」をチェックする。ここでは一体化時の設定をいじることもできる。

![窓オプション]({{ "/assets/images/2window04.png" | relative_url }})

## CFGファイルの取込

以下を編集して取込。これは[Configuration file & Memo](http://toro.d.dooo.jp/dlcfg.html)に記載されている設定。

```text
X_combo	= 1 ; 一体化窓有効
X_combos	= H42001,0
 ; H40021 タブ常時表示、１タブ
 ; Hc2021 タブ常時表示、ペイン毎にタブ、ペイン毎に独立タブ
 ; H42001 １ペイン１タブのときはタブ非表示、ペイン毎にタブ、各ペインのタブは共通内容

X_mpane	= 2,2 ; 1画面なら 1,1、2画面なら 2.2、1ペインでペイン数増加有なら 1,50
XC_page	= 1 ; 詳細表示用設定
XC_mvLR	= 4,1,4,B0100,0,B100 ; 左右カーソルで画面間移動
XC_celF	= {
A	= MwF16,5z10S1T14s1 ; 詳細表示用設定
}
```
