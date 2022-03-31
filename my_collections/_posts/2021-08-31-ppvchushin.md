---
title: PPv中心の連動ビュー
tag: ppv
---

1. PPcでEnterを押すとPPvが起動
1. PPvに連動させてPPcを操作
1. EnterでPPvを閉じる

```text
KV_main    = {    ; PPvメイン窓
LEFT    ,%K-C "@LEFT @N"
RIGHT    ,%K-C "@RIGHT @N"
UP    ,%K-C "@UP @N"
DOWN    ,%K-C "@DOWN @N"
SPACE    ,%K-C"@SPACE@N"
\SPACE    ,%K-C"@\SPACE@N"
ENTER ,%K"@Q"
}

E_cr = { ; [Enter]用判別
:JPEG ,
:BMP ,
:XJS ,
:XVBS ,
PNG ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
JPG ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
JPEG ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
BMP ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
GIF ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
TXT ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
CPP ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
H ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
C ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
L ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
EL ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
HTML ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
HTM ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
XYZZY ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
EMACS ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
SCM ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
INI ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
VBS ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
JS ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
HOWM ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
CFG ,%Obi *ppv -r %*name(CBD,"%R","%1") %: *focus "PPV["
}
```