---
title: 2画面
part: 2画面
date: 2023-01-13
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

以下を編集して取込する。

```text
X_combo = 1 ; 複数 PPc を一体化 0:しない 1:する
```
