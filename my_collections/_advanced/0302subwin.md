---
title: 展開・圧縮
part: サブ窓
created_at: 2023-01-13
last_modified_at: 2023-08-23
---

展開・圧縮をサブ窓を使ってできるようにする。

## 準備

以下を編集して取込。

```text{% raw %}
_Command	= {	; ユーザコマンド・関数
opensubwin	= *ppc -r -bootid:x -single -k *jumppath %*arg(1) %%: *mapkey use,K_subwin %%: *linemessage %*arg(2)
}

K_subwin	= {
\ENTER    ,*execute ,%*getcust(_User:temp_exec)
}

KC_main    = {
\U ,*setcust _User:temp_exec=*execute %n,*unpack %%1 %%: %%K"@Q"
	 *opensubwin %1,展開先のフォルダを選択してください
\P ,*setcust _User:temp_exec=*string o,name=%%"ファイル名を入力してください"%%{%%*extract(%n"%%%%X")%%} %%: *execute %n,*pack "!%%1%\%%so"name" %%: %%K"@Q"
	*opensubwin %1,圧縮先のフォルダを選択してください
\I ,*setcust _User:temp_exec=*execute %n,*pack "!%%1",indiv %%: %%K"@Q"
	*opensubwin %1,個別圧縮先のフォルダを選択してください
}{% endraw %}
```

## やり方

キーバインドは以下の通り。

- Shift+U : 展開
- Shift+P : 圧縮
- Shift+I : 個別圧縮

例えばhogehogeフォルダをTestフォルダに圧縮したいときは、以下のようになる。

hogehogeフォルダにカーソルを置く or マークする。

![hogehogeにカーソル]({{ "/assets/images/subwin04.png" | relative_url }})

Shift+PでPPc[X]が起動するので、Testフォルダへ移動してShift+Enter。

![サブ窓が起動]({{ "/assets/images/subwin05.png" | relative_url }})

一行編集に圧縮ファイル名を入力してENTER。

![一行編集にファイル名を入力]({{ "/assets/images/subwin06.png" | relative_url }})
