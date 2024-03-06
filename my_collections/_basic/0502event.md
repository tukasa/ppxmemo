---
title: ACTIVEEVENT
part: EVENT
created_at: 2023-01-19
last_modified_at: 2023-07-12
---
アクティブになったときに実行する。

- 窓のレイアウトの変更
- 窓同士の位置関係の調整

といった使い方がありうる。

_2画面一体化型のペイン比率を一定に_

```text
KC_main = {
ACTIVEEVENT , *pairrate 70
}
```

_PPcアクティブ時にすべてのPPvを閉じる_

```text
KC_main = {
ACTIVEEVENT , *closeppx V*
}
```
