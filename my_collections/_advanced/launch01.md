---
title: ランチャ
part: ランチャ
date: 2023-01-13
---

一行編集をランチャとして使う。

![ランチャ]({{ "/assets/images/launch01.png" | relative_url }})

## 準備

1) 以下をPPxフォルダに保存。

_l_cmd.txt_
```text
D:\bin
D:\Data
D:\bin\NeeView\NeeView.exe
D:\bin\nyanfi\NyanFi.exe
vivaldi http://toro.d.dooo.jp/slppx.html
*cliptext (」・ω・)」つかー！ (/・ω・)/にゃーん！
*ppb 
*ppc ;PPcを実行
*ppcust /edit %m編集して取込
*ppcust
*reboot ;Windows を再起動
*shutdown ;Windows をシャットダウン
*suspend ;サスペンド状態に移行
editor %0l_cmd.txt
```

2) 以下を編集して取込。

```text
_Command = { ; ユーザコマンド・関数
ppl = *string o,name=%*input("" -title:"PPlauncher" -mode:e -k:"*completelist /set /file:%%0l_cmd.txt") %:
 *ifmatch "o:e,a:d+",%so"name" %: *execute C,*jumppath "%so"name"" %: *stop
 *ifmatch "o:e,a:d-",%so"name" %: *execute ,"%so"name"" %: *stop
 *execute,%so"name"
}

K_tray = { ; PPtrayホットキー(キー指定 不可,V_xx 形式を推奨)
^' ' ,*focus !#%*findwindowtitle("PPlauncher"),%0\PPTRAYW.EXE -c *ppl
}
```

3) pptrayw.exe(pptray.exe)を実行、PPTrayを常駐させる。

## やり方

[Ctrl+Space]を押すと、一行編集が表示される。入力内容により、

- フォルダ→PPCで開く
- それ以外→コマンド実行

と分岐する。

