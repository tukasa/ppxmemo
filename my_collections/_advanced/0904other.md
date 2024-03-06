---
title: PPv
part: その他
created_at: 2024-03-06
last_modified_at: 
---

## マウスホイールでPPv表示ファイル切り替え

![PPvマウスホイールで表示ファイル切り替え]({{ "/assets/images/pppv.gif" | relative_url }})

PPvのホイール操作で、PPc上の前・次のファイルを表示する「_others:pppv」という設定がある。これをPPvの隠しメニューに登録する。以下を編集して取込。

```text
HM_ppv    = {    ; PPv
pppv    , _AUTO,_DBLU , *RotateCustomize _others:pppv,1,0 %: %K"loadcust"
}
```

隠しメニューのpppvをクリックすると、「PPvのホイール操作によるPPcの前・次のファイル表示」がトグルで切り替わる。

---

## PPv窓間移動

![PPv窓間移動]({{ "/assets/images/ppvtab.gif" | relative_url }})

[Tab]で起動中のPPvに順次フォーカスする。 以下をScriptフォルダにnextppv.jsという名前で保存。

<script src="https://gist.github.com/tukasa/bdf83622bea31904cc9383cc4b2184c3.js"></script>

以下を編集して取込。

```text
KV_main    = {    ; PPvメイン窓
TAB    ,*selectppx %*script(%0Script\nextppv.js)
}
```