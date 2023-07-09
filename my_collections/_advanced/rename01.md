---
title: リネーム
part: リネーム
created_at: 2023-01-20
last_modified_at: 2023-07-10
---

## 普通にリネーム

![リネームダイアログ]({{ "/assets/images/rename01.png" | relative_url }})

[R]でリネームできる。カーソル状態他は、X_eselで調整できる。僕は、選択を外して拡張子前にカーソルがいくようにしている。

## 外部ソフトに投げて一括リネーム

![一括リネーム]({{ "/assets/images/rename02.png" | relative_url }})

複数のファイルを一括リネームするときは、マークして- [LiName](https://www.vector.co.jp/soft/winnt/util/se429883.html)に投げる。好きなエディタでリネームできて便利。
[Paper Plane xUI まとめサイト](https://w.atwiki.jp/wiki6_ppx/pages/19.html)にあるBatchRename.jsもおすすめ。

## 連番

![ファイル名統一]({{ "/assets/images/rename06.png" | relative_url }})

ファイル名を連番にしたいときは、マークしてから[Shift+R]で一括リネームする。

```text
file\.*
```

コマンドの場合は以下。

```text
*file Rename -name:file\.*
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
