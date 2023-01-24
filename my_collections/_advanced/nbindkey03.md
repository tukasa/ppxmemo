---
title: ppeで2ストロークキー
part: nストロークキー
created_at: 2023-01-24
---
ppeを2ストロークキーにすることもできる。

以下を編集して取込。

```text
K_xyzzy1 = {
^X ,*setnextkey K_xyzzy2
}

K_xyzzy2 = {
S ,%K"@^S"
^C ,%k"&F4"
}
```

`*edit -k *mapkey use,K_xyzzy1`で起動したppeでは、以下の2ストロークキーが使える。

- [C-x s] ファイルを保存
- [C-x C-c] 閉じる
