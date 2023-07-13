---
title: CLOSEEVENT
part: EVENT
created_at: 2023-01-19
last_modified_at: 2023-07-12
---
窓を閉じた後の処理や、フォーカス制御などに使用する。
基本的には、フォーカス制御に用途を限定したほうがいい。ここに登録した処理が、シャットダウン等で実行されない可能性があるからだ。どうしてもCLOSEEVENTでしか実行できない処理を除き、FIRSTEVENT等に登録する方が適切だろう。

_PPv終了時にフォーカスをPPcに戻す_

```tex
KV_main = {
CLOSEEVENT,*focus C
}
```
