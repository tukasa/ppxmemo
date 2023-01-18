---
title: PPvを被せて表示
part: 2画面
date: 2023-01-13
---

PPvを一体化PPcに被せて表示する。

## 自窓に被せて表示

![自窓ppv]({{ "/assets/images/2window05.png" | relative_url }})

```text
E_cr = { ; [Enter]用判別
:JPEG ,
:BMP ,
:XJS ,
:XVBS ,
PNG ,*ppv -popup:%N %FDC
JPG ,*ppv -popup:%N %FDC
JPEG ,*ppv -popup:%N %FDC
BMP ,*ppv -popup:%N %FDC
GIF ,*ppv -popup:%N %FDC
TXT ,*ppv -popup:%N %FDC
}

KV_main    = {    ; PPvメイン窓
LEFT    ,%K-C"@LEFT@N"
RIGHT    ,%K-C"@RIGHT@N"
UP    ,%K-C"@UP@N"
DOWN    ,%K-C "@DOWN @N"
SPACE    ,%K-C"@SPACE@N"
\SPACE    ,%K-C"@\SPACE@N"
ENTER ,%K"@Q"
}
```

## 反対窓に被せて表示

![自窓ppv]({{ "/assets/images/2window06.png" | relative_url }})

```text
E_cr = { ; [Enter]用判別
:JPEG ,
:BMP ,
:XJS ,
:XVBS ,
PNG ,*ppv -popup:%N~ %FDC
JPG ,*ppv -popup:%N~ %FDC
JPEG ,*ppv -popup:%N~ %FDC
BMP ,*ppv -popup:%N~ %FDC
GIF ,*ppv -popup:%N~ %FDC
TXT ,*ppv -popup:%N~ %FDC
}

KV_main    = {    ; PPvメイン窓
LEFT    ,%K-C"@LEFT@N"
RIGHT    ,%K-C"@RIGHT@N"
UP    ,%K-C"@UP@N"
DOWN    ,%K-C "@DOWN @N"
SPACE    ,%K-C"@SPACE@N"
\SPACE    ,%K-C"@\SPACE@N"
ENTER ,%K"@Q"
}
```

## 一体化窓PPcに被せて表示

![自窓ppv]({{ "/assets/images/2window07.png" | relative_url }})

```text
E_cr = { ; [Enter]用判別
:JPEG ,
:BMP ,
:XJS ,
:XVBS ,
PNG ,*ppv -popup:%NC# %FDC
JPG ,*ppv -popup:%NC# %FDC
JPEG ,*ppv -popup:%NC# %FDC
BMP ,*ppv -popup:%NC# %FDC
GIF ,*ppv -popup:%NC# %FDC
TXT ,*ppv -popup:%NC# %FDC
}

KV_main    = {    ; PPvメイン窓
LEFT    ,%K-C"@LEFT@N"
RIGHT    ,%K-C"@RIGHT@N"
UP    ,%K-C"@UP@N"
DOWN    ,%K-C "@DOWN @N"
SPACE    ,%K-C"@SPACE@N"
\SPACE    ,%K-C"@\SPACE@N"
ENTER ,%K"@Q"
}
```
