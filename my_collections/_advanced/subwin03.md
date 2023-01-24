---
title: 拡張子判別の登録
part: サブ窓
created_at: 2023-01-13
last_modified_at: 2023-01-24
---

[Shift+Enter]の拡張子判別をサブ窓で登録できるようにする。
以下を編集して取込。

```text
KC_main	= {	; PPcメイン窓
\X	,%ME_subwin
}

E_subwin	= {
*	,*setcust _User:temp_exec=*setcust E_scr:%T,%(%FCD %%*name(CD,"%%R","%%1")%) %%: %%K"@Q"
	*ifmatch 0,0%*getcust(E_scr:%T) %: *opensubwin %FCD,EXEファイルを選択してください %: *stop
	*opensubwin %*regexp("%*getcust(E_scr:%T)","h/[a-zA-Z]:\\.*\.exe/"),EXEファイルを選択してください
}
```

登録したい拡張子のファイルにカーソルをあわせ、[Shift+X]でサブ窓が開く。サブ窓で関連付けたいEXEファイルにカーソルをあわせ、[Shift+Enter]で登録される。
