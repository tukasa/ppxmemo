---
title: Rename
part: Rename
date: 2023-01-20
---

## 普通にリネーム

![リネームダイアログ]({{ "/assets/images/rename01.png" | relative_url }})

Rを押して行うリネーム。一つのファイルをリネームしたいときに。

カーソル状態他は、X_eselでいじれる。僕は、選択を外して拡張子前にカーソルがいくようにしている。

## 外部ソフトに投げて一括リネーム

![一括リネーム]({{ "/assets/images/rename02.png" | relative_url }})

複数のファイルを一括リネームするときは、マークして- [LiName](https://www.vector.co.jp/soft/winnt/util/se429883.html)に投げる。好きなエディタでリネームできて便利。
[Paper Plane xUI まとめサイト](https://w.atwiki.jp/wiki6_ppx/pages/19.html)にあるBatchRename.jsもおすすめ。

## バラバラのファイル名を統一する

![ファイル名統一]({{ "/assets/images/rename03.png" | relative_url }})

ファイル名がバラバラなのを統一したいときは、マークしてからShift+Rを押して一括リネームする。

```text
s/.+\.(.+)/file\\.$1
```

とすればおｋ。拡張子はそのままで、それを除いたファイル名がfile＋連番になる。
連番の桁数やどの数値から始めるかもリネームダイアログで調整可能。

## 頭に連番を付ける

![連番リネーム]({{ "/assets/images/rename04.png" | relative_url }})

一括リネームで、次のようにすればおｋ。マークした順番に連番を振るので、音楽ファイルの並び順を調整したいときとかに使えるかもしれない。

```text
s/^/\\_
```

## ダイアログでマークファイルを順次リネーム

![順次リネーム]({{ "/assets/images/rename05.png" | relative_url }})

PPXSCR.TXTに載っているサンプルを使う。

```text
//!*script
var oldalst = PPx.Extract("%*getcust(XC_alst)");
PPx.Execute("*customize XC_alst=1,1,1,1,1");
PPx.EntryFirstMark;
do {
   if ( PPx.Execute("%K\"@R") != 0 ) break;
   PPx.EntryMark = 0;
}while( PPx.EntryFirstMark != 0 );
PPx.Execute("*customize XC_alst=" + oldalst);
```
