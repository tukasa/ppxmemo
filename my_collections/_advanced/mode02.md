---
title: FastCopyモード
part: モード
created_at: 2023-01-16
last_modified_at: 2023-06-01
---
コピー、移動、削除、ミラー処理に[FastCopy](https://fastcopy.jp/)を使う。
以下を編集して取込。

```text
A_exec	= {	; エイリアス
fastcopy	= D:\bin\FastCopy\fcp.exe
}

K_fastcopymode	= {
C	,%OB %'fastcopy' /cmd=update /auto_close /bufsize=1024 /error_stop /srcfile=%a*8FDC /to=%*input("%2" -title:"コピー先を指定してください - fastcopy mode -" -mode:d -select:l)\
M	,%OB %'fastcopy' /cmd=move /auto_close /bufsize=1024 /error_stop /srcfile=%a*8FDC /to=%*input("%2" -title:"移動先を指定してください - fastcopy mode -" -mode:d -select:l)\
D	,%OB %'fastcopy' /cmd=delete /auto_close /bufsize=1024 /error_stop /srcfile=%a*8FDC
F2	,%OB %'fastcopy' /cmd=sync /auto_close /bufsize=1024 /error_stop /srcfile=%a*8FDC /to=%*input("%2" -title:"ミラー先を指定してください - fastcopy mode -" -mode:d -select:l)\
ESC	, *mapkey delete,K_fastcopymode %: *linemessage FASTCOPY MODE END
}
```

以下のコマンドを実行すると、FastCopyモードになる。

```text
*mapkey use,K_fastcopymode %: *linemessage FASTCOPY MODE [C]COPY [M]MOVE [D]DELETE [F2]MIRROR [ESC]QUIT
```

キーバインドは以下のようになる。

- C: fastcopyでコピー
- M: fastcopyで移動
- D: fastcopyで削除
- F2: fastcopyでミラー処理
- Esc: モード終了
