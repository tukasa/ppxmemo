---
title: メニューTips
tags: 基本的なカスタマイズ
date: 2022-03-31
last_modified_at: 2022-03-31
---
## 階層化

![alt]({{ "/assets/images/menutips001.png" | relative_url }})

メニューにメニューを登録することで、階層化が可能。以下はHelpに載ってる例。

```text
KC_main = {
','  ,%M_exec
}

M_exec = {
&app1  = c:\bin\app1
app&2  = c:\bin\app2
app&3  = c:\bin\app3
その他  = %M_execsub
}

M_execsub = {
app&4  = c:\bin\app4
app&5  = c:\bin\app5
&shutdown  = *shutdown
}
```

## 特殊メニュー

![alt]({{ "/assets/images/menutips002.png" | relative_url }})

PPc一覧やドライブといった、特殊なメニューをメニュー項目に使うこともできる。
以下はHelpにあるサンプルメニュー。
「?yyy」と、?で始まる名前を記載するとメニューが下層として挿入。「??yyy」と、??で始まる名前を記載するとメニューが展開される。


```text
M_sample = {
PPc一覧 = ?ppclist
PPx一覧 = ?ppxidlist
レイアウト = ?layoutmenu
dock上 = ?docktmenu
ソート = ?sortmenu
表示 = ?viewmenu
作成 = ?newmenu
ドライブ = ?drivemenu
ドライブ表示 = ?drivelist
お気に入り = ?favorites
-- =
ここは使われない = ??M_pjump
}
```

## メニューとコマンドの組み合わせ

メニューは、他のコマンドと組み合わせることができる。
例えば、フォルダ履歴ジャンプメニューを自作する際、

```text
M_history = {
A  = %hp0
B  = %hp1
C  = %hp2
D  = %hp3
E  = %hp4
F  = %hp5
G  = %hp6
H  = %hp7
I  = %hp8
J  = %hp9
}

KC_main = {
H  ,%j%M_history,A
}
```

のようにもできるし、

```text
M_history = {
A  = %j %hp0
B  = %j %hp1
C  = %j %hp2
D  = %j %hp3
E  = %j %hp4
F  = %j %hp5
G  = %j %hp6
H  = %j %hp7
I  = %j %hp8
J  = %j %hp9
}

KC_main = {
H  ,%M_history,A
}
```

ともできるわけだ。

## 拡張子判別との組み合わせ

拡張子判別と組み合わせることで、拡張子ごとに専用のメニューを表示することができる。

テキストファイルであれば、それを投げるエディタ一覧をメニューで表示したり、画像ファイルであれば、それを投げるビューア一覧をメニューで表示したり、といったことができるわけだ。

これはテキストファイルの例。

![alt]({{ "/assets/images/menutips003.png" | relative_url }})

```text
E_scr    = {
TXT    ,%M_Text,X
INI    ,%M_Text,X
CFG    ,%M_Text,X
}

-|M_Text =

M_Text    = {
&xyzzy    = %Ob D:\bin\xyzzy\xyzzy.exe %FCD
&oedit    = %Ob D:\bin\oedit\oedit.exe %FCD
--    =
xyzzyで印刷(&P)    = %Ob D:\bin\xyzzy\xyzzy.exe -p %FCD
}
```

これは画像ファイルの例。

![alt]({{ "/assets/images/menutips004.png" | relative_url }})

```text
E_scr    = {
JPG    ,%M_Picture,A
PNG    ,%M_Picture,A
JPEG    ,%M_Picture,A
BMP    ,%M_Picture,A
}

-|M_Picture =

M_Picture    = {
&MassiGra    = %Ob D:\bin\MassiGra\MassiGra.exe %FCD
ペイント(&P)    = mspaint %FCD
--    =
壁紙にする(&W)    = *customize X_bg:Path=%FDC %: *customize X_bg:Type=10
}
```

## ショートカットキー

項目名のアルファベットの前に「&」を付けると、その文字がショートカットキーになる。

メニューを呼び出す際、`%M_test,s`のように「,」の後にショートカットキーを付けると、その項目を選択した状態でメニューが表示される。