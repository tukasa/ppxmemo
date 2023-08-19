---
title: ポータブル化
part: その他
created_at: 2023-01-16
---
## 基本

UNICODE版の場合は、「ユーザ名\AppData\Roaming\TOROID\PPx」にある「PPWC～.DAT」と「PPWH～.DAT」をPPxフォルダにコピーし、それぞれ「PPWCDEF.DAT」「PPWHDEF.DAT」とリネームする。

これが面倒だという場合は、PPxフォルダに空ファイルでPPWCDEF.DAT（Multibyte版ならPPXCDEF.DAT）を作成するだけでもいい。ただし、設定が初期化されるので、カスタマイザーの「テキストに書出」でPPX.CFGを作成してあらかじめ設定を保存しておく。

PPｘフォルダに空ファイルのPPWCDEF.DATがある状態で、PPxを起動すると 

![alt]({{ "/assets/images/portable01.png" | relative_url }})

このようなダイアログが出て、設定が初期化されるので、カスタマイザーの「テキストの取込」で先に作成したPPX.CFGを取り込む。

![alt]({{ "/assets/images/portable02.png" | relative_url }})

ファイルタブの下を見ると、Customize fileの場所がPPxフォルダのPPWCDEF.DATになってるはず。

## 相対パス

例えば僕は、Emacsをポータブル化してPPxと同階層に置いている。

ルート

```text
├─CatMemoNote
├─emacs
├─Palemoon-Portable
└─PPx2window
```

ドライブ名は環境によって変わることになるが、`%*name(H,%0)`で取得できる。なので、次のようにしてエディタのパスを指定する。

```text
A_exec    = {    ; エイリアス
editor    = %*name(H,%0)\emacs\bin\runemacs.exe
}
```

## 壁紙の設定

PPxフォルダに壁紙用の画像（kabegami.jpg）を入れ、それを壁紙にするようにする。

```text
X_bg = { 
Bright = 30
Type = 10
}

X_fles = 1 ; 画面のちらつき対策を 0:しない 1:する

KC_main = {
FIRSTEVENT , *customize X_bg:Path=%0\kabegami.jpg
}
```
