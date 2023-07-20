---
title: COMMENTEVENT
part: EVENT
created_at: 2023-01-15
last_modified_at: 2023-07-20
---

拡張コメントの内容が必要なときに使用する。以下の場合に呼び出される。

- 拡張コメントによるソートを実行
- 拡張コメントが含まれる表示形式に変更

COMMENTEVENTには`*comment`かスクリプトを登録する。COMMENTEVENTは1～10まで用意されており、それぞれを別々の用途に使うことができる。

```text
KC_main = { ; PPcメイン窓
COMMENTEVENT1 ,*comment 1,all extract,"拡張子=%%FT"
COMMENTEVENT2 ,*script %0Script\hoge.js
}
```

詳しくは[拡張コメント]({{ "/basic/other04" | relative_url }})を参照のこと。