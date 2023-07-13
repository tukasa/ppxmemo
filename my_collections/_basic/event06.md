---
title: COMMENTEVENT
part: EVENT
created_at: 2023-01-15
last_modified_at: 2023-07-14
---

主な用途は以下の2つだ。

- 特殊なソート
- エントリから取得した特殊な情報の表示

拡張コメントを利用する手順は、以下のようになる。

1. 拡張コメントを生成するスクリプトを作成
2. COMMENTEVENTにスクリプトを登録
3. ソートをCOMMENTEVENTに変更 or 表示形式をCOMMENTEVENTを含むものに変更

COMMENTEVENTは1～10まで用意されており、それぞれを別々の用途に用いることができる。

## 特殊なソート

EXE、TXT、CFG、ZIPを前方に。それ以外は後方に持ってくるようなソートをしてみよう。

以下をScriptフォルダに保存。

_excomment.js_
<script src="https://gist.github.com/tukasa/a5be598bfcd5508a8942cbbbc41c9549.js"></script>

以下を編集して取込。excomment.jsをCOMMENTEVENT1に登録する。

```text
KC_main = { ; PPcメイン窓
COMMENTEVENT1 ,*script %0Script\excomment.js
}
```

任意のディレクトリで以下を実行。ソートを拡張コメント1にする。

```text
*sortentry -thispath 24,1,0,B11111,1
```

ソートを拡張コメント1にしたディレクトリに行くと、excomment.jsが自動で実行された後、拡張コメントを用いたソートがなされることになる。
