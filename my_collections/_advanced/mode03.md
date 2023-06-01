---
title: 7-Zipモード
part: モード
created_at: 2023-01-16
last_modified_at: 2023-06-01
---
展開、圧縮に[7-Zip](https://sevenzip.osdn.jp/)を使う。
以下をScriptフォルダに保存。

_wrap_7z.js_
<script src="https://gist.github.com/tukasa/744d0df04bc3a95a2fc13ddff910cbaa.js"></script>

以下を編集して取込。

```text
A_exec	= {
7z	= "C:\Program Files\7-Zip\7z.exe"
}

K_7zipmode	= {
U	,*script %0\Script\wrap_7z.js,u,%a*8FCDN,%*input("%2" -title:"展開先を指定してください 7-Zip mode" -mode:d -select:l)
P	,*script %0\Script\wrap_7z.js,p,%a*8FCDN,%*input("%2%*addchar(\)|%*extract(C"%%X")|.zip" -title:"圧縮先を指定してください 7-Zip mode" -select:i)
I	,*script %0\Script\wrap_7z.js,ip,%a*8FCDN,%*input("%2" -title:"個別圧縮先を指定してください 7-Zip mode" -mode:d -select:l)
ESC	, *mapkey delete,K_7zipmode %: *linemessage 7-Zip MODE END
}
```

以下のコマンドを実行すると、7-Zipモードになる。

```text
*mapkey use,K_7zipmode %: *linemessage 7-Zip MODE [U]展開 [P]圧縮 [I]個別圧縮 [Esc]QUIT
```

F1を押すと7-Zipモードになり、一時的にキーバインドが

- U: 7-Zipで展開
- P: 7-Zipで圧縮
- I: 7-Zipで個別圧縮
- Esc: モード終了

となる。
