---
title: 7-ZIP
part: サブ窓
created_at: 2023-01-13
last_modified_at: 2023-01-24
---

7-ZIPを使い、解凍や圧縮をする。
以下をScriptフォルダに保存。

_wrap_7z.js_
<script src="https://gist.github.com/tukasa/744d0df04bc3a95a2fc13ddff910cbaa.js"></script>

以下を編集して取込。

```text
A_exec	= {	; エイリアス
7z	= "C:\Program Files\7-Zip\7z.exe"
}

KC_main    = {
\U ,*setcust _User:temp_exec=*script %0Script\wrap_7z.js,u,%%*extract(%n"%%%%a*8FCDN"),%%1 %%: %%K"@Q"
	 *opensubwin %FCD,展開先のフォルダを選択してください
\P ,*setcust _User:temp_exec=*script %0Script\wrap_7z.js,p,%%*extract(%n"%%%%a*8FCDN"),%(%*input("%1%*addchar(\)|%*extract(C"%%X")|.zip" -title:"7zipで圧縮" -select:i) %: %K"@Q"%)
	*opensubwin %FCD,圧縮先のフォルダを選択してください
\I ,*setcust _User:temp_exec=*script %0Script\wrap_7z.js,ip,%%*extract(%n"%%%%a*8FCDN"),%%1 %%: %%K"@Q"
	 *opensubwin %FCD,個別圧縮先のフォルダを選択してください
}
```

- \U: サブ窓を使って7-Zipで展開
- \P: サブ窓を使って7-Zipで圧縮
- \I: サブ窓を使って7-Zipで個別圧縮

となる。

