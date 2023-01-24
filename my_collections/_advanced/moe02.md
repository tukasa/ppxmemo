---
title: アウトラインプロセッサ化
part: howm
created_at: 2023-01-24
---

![アウトラインプロセッサ]({{ "/assets/images/howm03.png" | relative_url }})

以下の二つのファイルをScriptフォルダに保存する。

- MakeOutlineComment.js
- OutlineSort.js

<script src="https://gist.github.com/tukasa/ed85c8f8fcf8b6ce0b37e25c109cbf9d.js"></script>
<script src="https://gist.github.com/tukasa/cbbecf0f45e72d70e4b8febd435a0ca7.js"></script>

以下を編集して取込。

```text
{% raw %}
KC_main = { ; PPcメイン窓
^\LEFT ,*comment "%*regexp("%*comment","s/^\s?(.*)/$1/")"
^\RIGHT ,*comment "　%*comment"
^\DOWN = @DEL @INS @DOWN
^\UP = @UP @DEL @INS
F7    ,*script %0\Script\MakeOutlineComment.js
COMMENTEVENT1 ,*script %0Script\OutlineSort.js
}

MC_sort = {
拡張ソート&1 = 24,-1,-1,B11111,1
}
{% endraw %} 
```

対象フォルダで[S]を押してソートメニューを出し、「このパス以降」「拡張ソート1」を選択する。

![表示形式の変更]({{ "/assets/images/howm04.png" | relative_url }})

[H]を押し、出てきたウィンドウに`*diroption -thisbranch cmd:"*setcust XC_cwrt= 0"`を入力して実行する。これで、このフォルダ以下ではコメントファイルが自動作成されなくなる。後でこの設定を解除したくなったら、`*diroption -thisbranch cmd:""`とすればいい。
以上で準備は完了だ。エントリ位置やレベル調整はカーソルキーで行う。

- [Ctrl+Shift+カーソル上下] ：エントリ位置変更
- [Ctrl+Shift+カーソル左右] ：エントリレベル変更
- [F7] :変更の保存
