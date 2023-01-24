---
title: 7-Zipモード
part: モード
created_at: 2023-01-16
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

KC_main = {
F1	,*mapkey use,K_7zipmode %: *linemessage 7-Zip MODE: Press H for HELP
}

K_7zipmode	= {
U	,*script %0\Script\wrap_7z.js,u,%a*8FCDN,%2
P	,*script %0\Script\wrap_7z.js,p,%a*8FCDN,%*input("%2%*addchar(\)|%*extract(C"%%X")|.zip" -title:"7zipで圧縮" -select:i)
I	,*script %0\Script\wrap_7z.js,ip,%a*8FCDN,%2
\U ,*setcust _User:sorce_id=%n %: *ppc -r -bootid:x -single "%1" -k %(*mapkey use,K_subwin %: *linemessage 展開先を選択してください %: *string i,temp_exec=%(*script %0\Script\wrap_7z.js,u,%*extract(%su"sorce_id""%%a*8FCDN"),%1 %: %K"@Q"%)%)
\P ,*setcust _User:sorce_id=%n %: *ppc -r -bootid:x -single "%1" -k %(*mapkey use,K_subwin %: *linemessage 圧縮先を選択してください %: *string i,temp_exec=%(*script %0\Script\wrap_7z.js,p,%*extract(%su"sorce_id""%%a*8FCDN"),%*input("%1%*addchar(\)|%*extract(C"%%X")|.zip" -title:"7zipで圧縮" -select:i) %: %K"@Q"%)%)
\I ,*setcust _User:sorce_id=%n %: *ppc -r -bootid:x -single "%1" -k %(*mapkey use,K_subwin %: *linemessage 展開先を選択してください %: *string i,temp_exec=%(*script %0\Script\wrap_7z.js,ip,%*extract(%su"sorce_id""%%a*8FCDN"),%1 %: %K"@Q"%)%)
ESC	, *mapkey delete,K_7zipmode %: *linemessage 7-Zip MODE END
H	, %"7-Zip mode"%I"U%bt:展開%bnP%bt:圧縮%bnI%bt:個別圧縮%bn\U%bt:サブ窓で展開%bn\P%bt:サブ窓で圧縮%bn\I%bt:サブ窓で個別圧縮%bnESC%bt:モード終了"
}

K_subwin	= {
\ENTER    ,*execute ,%si"temp_exec"
}
```
F1を押すと7-Zipモードになり、一時的にキーバインドが

- U: 7-Zipで展開
- P: 7-Zipで圧縮
- I: 7-Zipで個別圧縮
- \U: サブ窓を使って7-Zipで展開
- \P: サブ窓を使って7-Zipで圧縮
- \I: サブ窓を使って7-Zipで個別圧縮
- H: ヘルプ表示
- Esc: モード終了

となる。
