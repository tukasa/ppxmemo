---
title: 一時コマンド
part: nストロークキー
date: 2023-01-13
---
スクリプトを作っている時や、新しいコマンドを試している時に、一時的に特定のコマンドをキーに登録したい場合がある。

通常は、HやXを押してコマンドを打ち込み、実行というのを一々繰り返したり、カスタマイザで通常は使用しないキーにコマンドを登録したり、ということをするのだが、この過程を省略したい。そこで、

- 一時的にコマンドを記憶
- 特定のキーでそれを実行

ができるようにする。

```text
{% raw %}
KC_main = { ; PPcメイン窓
^Z ,*setnextkey K_launcher
}

K_launcher = { ** comment **
Z ,*alias temp_cmd = %"一時コマンド"%{%'temp_cmd'%}
^Z ,*execute ,%'temp_cmd'
}
{% endraw %}
```

C-z z（Ctrl+Zを押したあとZを押す）で記憶させたいコマンドを打ち込む。
C-z C-z（Ctrl+Zを二回押し）で、記憶させたコマンドを実行する。