---
title: PPe
part: その他
created_at: 2023-12-26
last_modified_at: 
---

PPeは簡易テキストエディタ。起動が早いので、ちょっとしたテキストの修正に便利。

## 前回閉じた位置を再現

[^W]で、現在の位置と大きさを保存したあと閉じる。次回起動時は、前回の位置と大きさが再現される。

```text
_Command	= {	; ユーザコマンド・関数
savepos	= *setcust %*arg(1):l=%*windowrect(,l)
 *setcust %*arg(1):t=%*windowrect(,t)
 *setcust %*arg(1):w=%*windowrect(,w)
 *setcust %*arg(1):h=%*windowrect(,h)
loadpos	= *string o,fuga=%*arg(1)
 *windowposition %N.,%*getcust(%so"fuga":l),%*getcust(%so"fuga":t),%*getcust(%so"fuga":w),%*getcust(%so"fuga":h)
}

K_ppe	= {	; PPe(K_ppeに該当しない場合はK_edit参照)
^W	,*savepos S_ppepos %: %k"&F4"
FIRSTEVENT	,*loadpos S_ppepos
}
```

## PPVからPPeを開いた際、現在行へジャンプする

キャレットモード時に[E]でPPeを開き、現在行にジャンプする。

```text
KV_crt	= {	; PPvテキスト(キャレット)追加設定
E	,*edit %FCD -k *cursor -17, 0, %%L
}
```
