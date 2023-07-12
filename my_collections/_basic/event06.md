---
title: COMMENTEVENT
part: EVENT
created_at: 2023-01-15
last_modified_at: 
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
<script src="https://gist.github.com/tukasa/a5be598bfcd5508a8942cbbbc41c9549.js"></script>

以下を編集して取込して、このスクリプトをCOMMENTEVENT1に登録する。

```text
KC_main = { ; PPcメイン窓
COMMENTEVENT1 ,*script %0Script\excomment.js
}
```

任意のフォルダで以下を実行する。

`*sortentry -thispath 24,1,0,B11111,1`

すると、COMMENTEVENT1が呼び出され、excomment.jsが実行された後に、拡張コメントを用いたソートがなされる。
