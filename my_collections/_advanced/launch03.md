---
title: ランチャ化
part: 一行編集の活用
created_at: 2023-01-25
---

PPtrayを利用することで、ホットキーを用いて一行編集を表示することができる。これにより、ランチャとして使うことが可能になる。
以下を編集して取込。

```text
K_tray	= {	; PPtrayホットキー(キー指定 不可,V_xx 形式を推奨)
V_HE5	,%0\PPTRAYW.EXE -c *ppl
}
```

PPTRAYW.EXEを実行、PPTrayを常駐させておく。
これにより、CapsLockで一行編集を表示することができる。
ちなみに、表示非表示をトグルで切り替えたい場合は以下のようになる。

```text
K_tray	= {	; PPtrayホットキー(キー指定 不可,V_xx 形式を推奨)
V_HE5	,*focus !#%*findwindowtitle("PPlauncher"),%0PPTRAYW.EXE -c *ppl
}
```


