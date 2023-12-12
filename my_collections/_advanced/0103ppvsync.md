---
title: 一対一対応かつ多重起動禁止
part: PPv中心の連動ビュー
created_at: 2023-12-13
last_modified_at: 
---

一対一対応したPPvが既にある場合は、それを利用する。

<script src="https://gist.github.com/tukasa/c6b7cb1d8c44424d2d4822f74d2a7aca.js"></script>

```text
_Command	= {	; ユーザコマンド・関数
myppv	= *ifmatch 0,0%*script(%0Script\checkppcid.js) %: *ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1) %: *stop
*ppv -bootid:%*script(%0Script\checkppcid.js) %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
}
```
