---
title: コピー・移動
part: サブ窓
created_at: 2023-01-13
last_modified_at: 2024-03-17
---

コピー先・移動先のフォルダをサブ窓を使って指定できるようにする。

![サブ窓による移動]({{ "/assets/images/subwin01.gif" | relative_url }})

## 準備

以下を編集して取込。

```text
_Command	= {	; ユーザコマンド・関数
opensubwin	= *ppc -r -bootid:x -single -k *jumppath %*arg(1) %%: *mapkey use,K_subwin %%: *linemessage %*arg(2)
}

K_subwin	= {
\ENTER    ,*execute ,%*getcust(_User:temp_exec)
}

KC_main    = {
\M ,*setcust _User:temp_exec=*file !move ,%%*extract(%n"%%%%@*8FCDN"),%%1 %%: %%K"@Q"
	*ifmatch "o:e,a:d",%FD %: *opensubwin %FD,移動先のフォルダを選択してください %: *stop
	*opensubwin %0,移動先のフォルダを選択してください
\C ,*setcust _User:temp_exec=*file !copy ,%%*extract(%n"%%%%@*8FCDN"),%%1 %%: %%K"@Q"
	*ifmatch "o:e,a:d",%FD %: *opensubwin %FD,コピー先のフォルダを選択してください %: *stop
	*opensubwin %0,コピー先のフォルダを選択してください
}
```

## やり方

キーバインドは以下の通り。

- Shift+C : コピー
- Shift+M : 移動

例えばaaa.txtをhogehogeフォルダに移動したい場合は、以下のようになる。

aaa.txtにカーソルを置く or マークする。

![操作対象にカーソル]({{ "/assets/images/subwin02.png" | relative_url }})

Shift+MでPPc[X]が起動するので、hogehogeフォルダへ移動してShift+Enter。

![PPCXが起動]({{ "/assets/images/subwin03.png" | relative_url }})

