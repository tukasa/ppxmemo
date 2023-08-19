---
title: ホットキー
part: 一行編集
created_at: 2023-01-25
last_modified_at: 2023-08-19
---

PPtrayを利用することで、ホットキーを用いて一行編集を表示することができる。
以下を編集して取込。

```text
_Command = { ; ユーザコマンド・関数
ppl = *string o,name=%*input("" -title:"PPlauncher" -mode:h -leavecancel -k:"*completelist /set /file:%%0launch.txt")
  *execute,%so"name"
}

K_tray	= {	; PPtrayホットキー(キー指定 不可,V_xx 形式を推奨)
V_HE5	,%0\PPTRAYW.EXE -c *ppl
}
```

PPTRAYW.EXEを実行、PPTrayを常駐させておく。
これにより、[CapsLock]で一行編集を表示することができる。
ちなみに、表示非表示を[CapsLock]のトグルで切り替えたい場合は以下のようになる。

```text
_Command = { ; ユーザコマンド・関数
ppl = *string o,name=%*input("" -title:"PPlauncher" -mode:h -leavecancel -k:"*completelist /set /file:%%0launch.txt")
  *execute,%so"name"
}

K_tray	= {	; PPtrayホットキー(キー指定 不可,V_xx 形式を推奨)
V_HE5	,*focus !#%*findwindowtitle("PPlauncher"),%0PPTRAYW.EXE -c *ppl
}
```


