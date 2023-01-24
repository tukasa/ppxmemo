---
title: DockShow
part: module
created_at: 2022-03-31
last_modified_at: 
---
DockShowは、Paper Plane xUI のウィンドウに埋め込んで使用するためのメディアプレイヤー。

## 登録

DockShowをダウンロードしたあと、中にあるDockShow.EXE（DockShow64.EXE）をPPxフォルダに置く。

次いで、上の位置に埋め込みたいなら、以下を実行。

※これより先、64bit版を使ってる場合はDockShow.EXEをDockShow64.EXEに読み替えてください

```text
*dock add,t,%0\DockShow.EXE
```

編集して取込の場合は、次のようになる。

```text
X_dock = { ; バー割当て(要IE4以降)*layout,*dock
CA_T = D:\bin\ppx2window64\\DockShow.EXE,100,0
}
```

これで、次のようになる。

![alt]({{ "/assets/images/dockshow01.png" | relative_url }})

メニューバーの下にあるのが DockShow。

削除するときは、`*dock delete,t,DockShow`を実行する。
ちなみに、下の位置に埋め込みたいなら`*dock add,b,%0\DockShow.EXE`とする。t(top)をb(bottom)に変えればいいわけだ。

## 使い方

上の位置に埋め込んだ場合、音楽ファイルにカーソルをあわせ、`*dock drop,t,DockShow`とすれば、それを再生する。マウスでのドラッグ＆ドロップでもいい。

![alt]({{ "/assets/images/dockshow02.png" | relative_url }})

 左クリックで一時停止。右クリックで音量を調整できる。

![alt]({{ "/assets/images/dockshow03.png" | relative_url }})

## SELECTEVENT

SELECTEVENTに登録すると、カーソルの動きと連動させて、音楽ファイルを再生することができる。カーソルを動かせば、それと連動して、カーソル下のファイルをDockShowで自動再生するわけだ。

まずは、以下を編集して取込。これは上に埋め込んでいる場合。もし、下に埋め込んでいるなら、tをbに変えよう。

```text
E_syncevent = { 特製連動表示
AVI ,*dock drop,t,DockShow
MP2 ,*dock drop,t,DockShow
MP3 ,*dock drop,t,DockShow
MPG ,*dock drop,t,DockShow
WMA ,*dock drop,t,DockShow
WMV ,*dock drop,t,DockShow
WM ,*dock drop,t,DockShow
ASF ,*dock drop,t,DockShow
MID ,*dock drop,t,DockShow
}
```

ついで、`*linecust ^syncevent,KC_main:SELECTEVENT,%%ME_syncevent`を適当なキーに登録する。これで、カーソルと音楽再生の連動ON/OFFが、トグルでできるようになる。

