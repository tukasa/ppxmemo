---
title: サブ窓によるコピーと移動
part: サブ窓
date: 2023-01-13
---

サブ窓で操作先のフォルダを選択できるようにする。

## 準備

```text
_Command	= {	; ユーザコマンド・関数
opensubwin	= *ppc -r -bootid:x -single -k *jumppath %*arg(1) -entry %%: *fitwindow %NC,%%NC,20 %%: *mapkey use,K_subwin %%: *linemessage %*arg(2)
}

KC_main    = {
\M ,*setcust _User:temp_exec=*file !move ,%%*extract(%n"%%%%@*8FCDN"),%%1 %%: %%K"@Q"
	*opensubwin %FCD,移動先のフォルダを選択してください
\C ,*setcust _User:temp_exec=*file !copy ,%%*extract(%n"%%%%@*8FCDN"),%%1 %%: %%K"@Q"
	*opensubwin %FCD,コピー先のフォルダを選択してください}

K_subwin	= {
\ENTER    ,*execute ,%si"temp_exec"
}
```

## やり方

例えばaaa.txtをhogehogeフォルダに移動したい場合、以下の動作になる。


- aaa.txtにカーソルを置く or マークする。
- [Shift+M]を押すと、サブ窓PPc[X]が起動する。
- サブ窓PPc[X]でhogehogeフォルダへ移動して、[Shift+Enter]を押す。

![サブ窓による移動]({{ "/assets/images/subwin01.gif" | relative_url }})
