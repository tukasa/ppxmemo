---
title: ハイライトモード
part: モード
created_at: 2023-01-16
last_modified_at: 2023-08-15
---
ハイライトを使いやすいよう、キーバインドを一時的に変更する。また、ハイライトを保存、再現できるようにする。

![highlight mode ppc]({{ "/assets/images/highlightmode01.png" | relative_url }})

以下を編集して取込。

```text
-|K_highlightmode =

K_highlightmode = {
SPACE	,*if !%si"hlnum" %: %K"@SPACE" %: *stop
	*if %*js("PPx.result=PPx.EntryHighlight") %: *markentry -highlight:0 path:,%R %: %K"@DOWN" %: *stop
	*markentry -highlight:%si"hlnum" path:,%R %: %K"@DOWN"
\SPACE	,*if !%si"hlnum" %: %K"@\SPACE" %: *stop
	*if %*js("PPx.result=PPx.EntryHighlight") %: *markentry -highlight:0 path:,%R %: %K"@UP" %: *stop
	*markentry -highlight:%si"hlnum" path:,%R %: %K"@UP"
^S	, *makelistfile 00_LISTFILE.txt -basic -highlight %: *linemessage ハイライトを保存しました
ESC	, *linecust highlight,KC_main:LOADEVENT, %: *mapkey delete,K_highlightmode %: *linemessage HIGHLIGHT MODE END
0	, *linemessage ファイルマークに変更しました %: *string i,hlnum=0
1	, *linemessage ハイライト1に変更しました %: *string i,hlnum=1
2	, *linemessage ハイライト2に変更しました %: *string i,hlnum=2
3	, *linemessage ハイライト3に変更しました %: *string i,hlnum=3
4	, *linemessage ハイライト4に変更しました %: *string i,hlnum=4
5	, *linemessage ハイライト5に変更しました %: *string i,hlnum=5
6	, *linemessage ハイライト6に変更しました %: *string i,hlnum=6
7	, *linemessage ハイライト7に変更しました %: *string i,hlnum=7
}
```

以下のコマンドを実行すると、ハイライトモードになる。

```text
*linecust highlight,KC_main:LOADEVENT,*ifmatch "o:e,a:d-","00_LISTFILE.txt" %%: *markentry -set:00_LISTFILE.txt %: *mapkey use,K_highlightmode %: *string i,hlnum=1 %: *linemessage HIGHLIGHT MODE [1-7]CHANGE COLOR ^[S]SAVE [ESC]QUIT
```

キーバインドは以下のようになる。

- [SPACE] カーソル位置のファイルをハイライト & [↓]
- \\[SPACE] カーソル位置のファイルをハイライト & [↑]
- [数字] ハイライト色切り替え
- ^[S] ハイライトを00_LISTFILE.txtに保存
- [ESC] ハイライトモード終了

また、00_LISTFILE.txtがディレクトリにあれば、ハイライトを自動で再現する。
