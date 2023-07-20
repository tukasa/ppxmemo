---
title: 拡張コメント
part: その他
created_at: 2023-01-15
last_modified_at: 2023-07-20
---

拡張コメントの主な用途は以下の二つだ。

- 特殊なソート
- エントリから取得した特殊な情報の表示

拡張コメントを利用する手順は、以下の通り。

1. COMMENTEVENTに`*comment` or スクリプトを登録
2. ソートをCOMMENTEVENTに変更 or 表示形式をCOMMENTEVENTを含むものに変更

## 特殊なソート

拡張コメントを用いて、EXE、TXT、CFG、ZIPを前方に。それ以外は後方に持ってくるソートをしてみよう。

### *commentの場合

以下を編集して取込。

```text
-|E_comment1=

E_comment1	= {
EXE	,1
TXT	,2
CFG	,3
ZIP	,4
*	,5
}

KC_main = { ; PPcメイン窓
COMMENTEVENT1 ,*comment 1,all extract,"%%ME_comment1"
}
```

任意のディレクトリで以下を実行し、ソートを拡張コメント1にする。

```text
*sortentry -thispath 24,1,0,B11111,1
```

ソートを拡張コメント1にしたディレクトリに行くと、`COMMENTEVENT1`を自動で実行した後、拡張コメント1によるソートが行われる。

### スクリプトの場合

以下をScriptフォルダに保存。

_excomment.js_
<script src="https://gist.github.com/tukasa/a5be598bfcd5508a8942cbbbc41c9549.js"></script>

以下を編集して取込。excomment.jsをCOMMENTEVENT1に登録する。

```text
KC_main = { ; PPcメイン窓
COMMENTEVENT1 ,*script %0Script\excomment.js
}
```

任意のディレクトリで以下を実行し、ソートを拡張コメント1にする。

```text
*sortentry -thispath 24,1,0,B11111,1
```

ソートを拡張コメント1にしたディレクトリに行くと、`COMMENTEVENT1`を自動で実行した後、拡張コメント1によるソートが行われる。
