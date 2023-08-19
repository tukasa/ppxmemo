---
title: 反対窓にフォルダ内容を表示
part: モード
created_at: 2023-06-11
last_modified_at: 
---
現在窓のカーソルに連動して、反対窓にカーソル下フォルダの内容を表示する。

![反対窓にフォルダ内容表示]({{ "/assets/images/openbyotherwin01.gif" | relative_url }})

以下を編集して取込。

```text
K_openbyotherwin    = {
ESC    ,*mapkey delete,K_openbyotherwin %: *linecust obow,KC_main:SELECTEVENT, %: *linemessage Open by other Window MODE END
}
```

以下を実行する。

```text
*mapkey use,K_openbyotherwin %: *string i,ppcid=%N %: *linecust obow,KC_main:SELECTEVENT,*ifmatch !0,0%(%si"ppcid" %: *execute ~,%%j%FCD%) %: %K"loadcust" %: *linemessage  Open by other Window MODE [ESC]QUIT
```

モードを終了したい場合は[ESC]。
