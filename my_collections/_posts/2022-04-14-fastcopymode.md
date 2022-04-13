---
title: FastCopyモード
author: tukasa
tag: mode
---
コピー、移動、削除、ミラー処理に[FastCopy](https://fastcopy.jp/)を使う。

```text
A_exec	= {	; エイリアス
fastcopy	= D:\bin\FastCopy\fcp.exe
}

KC_main = {
F1	,*mapkey use,K_fastcopymode %: *linemessage FASTCOPY MODE: Press H for HELP
}

K_fastcopymode	= {
C	,%OB %'fastcopy' /cmd=update /auto_close /bufsize=1024 /error_stop /srcfile=%a*8FDC /to=%*input("%2" -title:"コピー先を指定してください" -mode:d -select:l)\
M	,%OB %'fastcopy' /cmd=move /auto_close /bufsize=1024 /error_stop /srcfile=%a*8FDC /to=%*input("%2" -title:"移動先を指定してください" -mode:d -select:l)\
D	,%OB %'fastcopy' /cmd=delete /auto_close /bufsize=1024 /error_stop /srcfile=%a*8FDC
F2	,%OB %'fastcopy' /cmd=sync /auto_close /bufsize=1024 /error_stop /srcfile=%a*8FDC /to=%*input("%2" -title:"ミラー先を指定してください" -mode:d -select:l)\
ESC	, *mapkey delete,K_fastcopymode %: *linemessage FASTCOPY MODE END
H	, %"fastcopy mode"%I"C%bt:コピー%bnM%bt:移動%bnD%bt:削除%bnF2%bt:ミラー処理%bnESC%bt:モード終了"
}
```

F1を押すとFastCopyモードになり、一時的にキーバインドが

- C: fastcopyでコピー
- M: fastcopyで移動
- D: fastcopyで削除
- F2: fastcopyでミラー処理
- H: ヘルプ表示
- Esc: モード終了

となる。