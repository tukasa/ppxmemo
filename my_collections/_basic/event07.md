---
title: RANGEEVENT
part: EVENT
created_at: 2022-03-31
last_modified_at: 2023-01-24
---
エントリカーソル移動カスタマイズで、デフォルトにない動作や、分岐など複雑なことをしたいときは、RANGEEVENTを使う。

```text
XC_mvLR = 4,1,4,B0000,16,B0000

KC_main = {
RANGEEVENT1 ,*linemessage rangeevent1
RANGEEVENT2 ,*linemessage rangeevent2
}
```

こうすると、カーソル左右で範囲外移動をしたときに KC_main の RANGEEVENT1 / RANGEEVENT2 が呼び出されるようになる。

## PPcからPPcに窓間移動

![PPcからPPvに窓間移動]({{ "/assets/images/rangeevent01.gif" | relative_url }})

二画面で反対窓にPPvを被せて表示している時用の設定。PPvが表示されていればPPvにフォーカスを。そうでなければ窓間移動をさせる。

```text
XC_mvLR = 4,1,16,B0000,16,B0000

KC_main = {
RANGEEVENT1 ,*ifmatch %NC,%NC#L %: %K"@BS" %: *stop
 *ifmatch 0,0%NVY %: %K"@TAB" %: *stop
 *focus VY
RANGEEVENT2 ,*ifmatch %NC,%NC#R %: %K"@BS" %: *stop
 *ifmatch 0,0%NVY %: %K"@TAB" %: *stop
 *focus VY
}

KV_page = { ; PPvテキスト(ページ)追加設定
LEFT ,*focus C
RIGHT ,*focus C
}
```
