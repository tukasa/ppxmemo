---
title: 拡張コメント
author: tukasa
tag: event
---
コメントを一時処理に利用したい時は、COMMENTEVENTを利用する。

大まかには

1. 拡張コメントを生成するスクリプトを用意
2. それをCOMMENTEVENTに登録
3.  ソートあるいは表示形式を変更する

という流れ。COMMENTEVENTは1～10まで用意されており、別々の用途に用いることができる。

例えば、EXE、TXT、CFG、ZIPを前方に。それ以外は後方に持ってくるようなソートをしたい場合は次のようにする。

以下をScriptフォルダに保存。

_excomment.js_

```text
//!*script

for (var i = 0; i < PPx.EntryAllCount; i++) {
  if (PPx.Entry(i).Name.match(/.EXE$/i)) {
    PPx.Entry(i).SetComment(1,1);
  } else if (PPx.Entry(i).Name.match(/.TXT$/i)) {
    PPx.Entry(i).SetComment(1,2);
  } else if (PPx.Entry(i).Name.match(/.CFG$/i)) {
    PPx.Entry(i).SetComment(1,3);
  } else if (PPx.Entry(i).Name.match(/.ZIP$/i)) {
    PPx.Entry(i).SetComment(1,4);
  } else {
    PPx.Entry(i).SetComment(1,5);
  }
}
```

以下を編集して取込して、このスクリプトをCOMMENTEVENT1に登録する。

```text
KC_main = { ; PPcメイン窓
COMMENTEVENT1 ,*script %0\Script\excomment.js
}
```

任意のフォルダで以下を実行する。

`*sortentry -thispath 24,1,0,B11111,1`

すると、COMMENTEVENT1が呼び出され、excomment.jsが実行された後に、拡張コメントを用いたソートがなされる。
