---
title: CLOSEEVENT
part: EVENT
created_at: 2023-01-19
last_modified_at: 2023-07-12
---
窓を閉じた後の処理や、フォーカス制御などに使用する。
シャットダウン等により、CLOSEEVENTに登録した処理が実行されない可能性がある。FIRSTEVENTでも実行できる処理であれば、FIRSTEVENTに登録した方がいい。CLOSEEVENTは基本的にフォーカス制御に用途を限定し、他にはどうしてもCLOSEEVENTでしか実行できない処理のみを登録するのが適切だろう。

_PPv終了時にフォーカスをPPcに戻す_

```tex
KV_main = {
CLOSEEVENT,*focus C
}
```
