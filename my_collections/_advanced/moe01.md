---
title: howmファイルのタイトル表示
part: howm
created_at: 2023-01-13
---

howm形式のファイルをタイトル表示する。howmとPPxの組み合わせについては、[moe](https://tukasa.github.io/moe/)も参照のこと。

![howmのタイトル表示]({{ "/assets/images/howm01.png" | relative_url }})

## 準備

以下をScriptフォルダに保存。

_title2comment_all.js_

<script src="https://gist.github.com/tukasa/c8805f8ef34cd85af659499bc0c91ae4.js"></script>

以下を編集して取込。

```text
{% raw %}
KC_main    = {	; PPcメイン窓
F6    ,*script %0Script\title2comment_all.js %: *setcust XC_cwrt= 2
}

MC_celS    = {    ; エントリ表示 書式([;]メニュー)
howmtitle    = M cF25,6 w35C z7 S1 tC"y-N-D" s1
}
{% endraw %} 
```

## やり方

[;]で表示形式メニューを表示し、「このパス以降」「howmtitle」を選択したあと、[F6]を押す。
新規作成したメモは、作成後に[F6]を押すことでタイトル表示に反映することができる。

![表示形式の変更]({{ "/assets/images/howm02.png" | relative_url }})

