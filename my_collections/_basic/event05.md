---
title: SELECTEVENT
part: EVENT
created_at: 2023-01-19
last_modified_at: 2023-07-12
---
カーソル移動にあわせた連携処理に使用する。

- PPvによる連動ビュー
- 連動プロパティ表示
- ファイルの詳細情報の連動
- 連動パス・表示パス同期

についてはデフォルトでできるので、これ以外の特殊な連動をPPx内で行うか、あるいは外部アプリケーションとの連動に使うか、ということになるだろう。
前者の例としては、[反対窓にフォルダ内容を表示]({{ "/advanced/mode04" | relative_url }})や[DockShow]({{ "/basic/module04" | relative_url }})を参考にしてほしい。

_MassiGraとの連動_

```text
KC_main = {
SELECTEVENT,%Obi D:\bin\MassiGra\MassiGra.exe %FCD %: *focus C
}
```
