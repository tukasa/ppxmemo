---
title: ハイライトモード
part: モード
created_at: 2023-01-16
---
キーバインドを一時的にハイライトモードに変更。ハイライトを使いやすくする。
また、ハイライトを保存、再現できるようにする。

![highlight mode ppc]({{ "/assets/images/highlightmode.gif" | relative_url }})

以下を編集して取込。

```text
KC_main = {
F1	,*mapkey use,K_highlightmode %: *linemessage HIGHLIGHT MODE: Press H for HELP
}

K_highlightmode = {
SPACE	, *markentry -highlight:1 %R %: %K"@DOWN"
\SPACE	, *markentry -highlight:0 %R %: %K"@UP"
^S	, *makelistfile 00_LITFILE.txt -basic -highlight
H	, %"highlight mode"%I"SPACE%bt:ハイライト%bn\SPACE%bt:ハイライト解除%bn1~7 %bt:指定ハイライトの変更%bn^S%bt:ハイライトの保存%bnESC%bt:ハイライトモード終了"
ESC	, *mapkey delete,K_highlightmode %: *linemessage HIGHLIGHT MODE END
1	, *linemessage ハイライト1に変更しました %: *setcust K_highlightmode:SPACE,*markentry -highlight:1 %%R %%: %%K"@DOWN"
2	, *linemessage ハイライト2に変更しました %: *setcust K_highlightmode:SPACE,*markentry -highlight:2 %%R %%: %%K"@DOWN"
3	, *linemessage ハイライト3に変更しました %: *setcust K_highlightmode:SPACE,*markentry -highlight:3 %%R %%: %%K"@DOWN"
4	, *linemessage ハイライト4に変更しました %: *setcust K_highlightmode:SPACE,*markentry -highlight:4 %%R %%: %%K"@DOWN"
5	, *linemessage ハイライト5に変更しました %: *setcust K_highlightmode:SPACE,*markentry -highlight:5 %%R %%: %%K"@DOWN"
6	, *linemessage ハイライト6に変更しました %: *setcust K_highlightmode:SPACE,*markentry -highlight:6 %%R %%: %%K"@DOWN"
7	, *linemessage ハイライト7に変更しました %: *setcust K_highlightmode:SPACE,*markentry -highlight:7 %%R %%: %%K"@DOWN"
}
```

F1を押すとハイライトモードになり、一時的にキーバインドが

- SPACE	:ハイライト
- \SPACE	:ハイライト解除
- 1~7	:指定ハイライトの数値変更
- ^S	:ハイライトの保存（フォルダ内に00_LISTFILE.txtを作成）
- H	:ヘルプ表示
- ESC	:ハイライトモード終了

となる。

Ctrl+Sで00_LISTFILE.txtに保存したハイライトを再現したい場合は`*markentry -set:00_LITFILE.txt`とすればいい。
例えば特定のディレクトリで、00_LITFILE.txtが存在すればハイライトを再現するようにしたいなら、次のようになる。

```text
*diroption -thispath cmd:"*ifmatch ""o:e,a:d-"",""00_LITFILE.txt"" %: *markentry -set:00_LITFILE.txt"
```
