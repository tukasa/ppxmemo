---
title: PPcで一時コマンド
part: nストロークキー
created_at: 2023-01-13
---

![一時コマンド]({{ "/assets/images/nstrokekey01.png" | relative_url }})

PPcで以下ができるようにする。

- [C-z z]   コマンドを登録
- [C-z C-z] 登録したコマンドを実行

新しいコマンドを試したり、マクロの内容を確認するときに便利。

```text
{% raw %}
KC_main = {
^Z ,*setnextkey K_launcher
}

K_launcher = {
Z ,*setcust _User:temp_cmd = %"一時コマンド"%{%*getcust(_User:temp_cmd)%}
^Z ,*execute ,%*getcust(_User:temp_cmd)
}
{% endraw %}
```
