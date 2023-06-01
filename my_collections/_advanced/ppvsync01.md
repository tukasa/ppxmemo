---
title: 基本編
part: PPv中心の連動ビュー
created_at: 2023-01-13
last_modified_at: 2023-06-01
---

連動ビューをPPvにフォーカスを当てた状態で行う。

![ppvの連動ビュー]({{ "/assets/images/ppvsync01.png" | relative_url }})

## 準備

以下を編集して取込。

```text
E_cr = { ; [Enter]用判別
:JPEG ,
:BMP ,
:XJS ,
:XVBS ,
PNG ,*ppv %*name(CD,"%R","%1")
JPG ,*ppv %*name(CD,"%R","%1")
JPEG ,*ppv %*name(CD,"%R","%1")
BMP ,*ppv %*name(CD,"%R","%1")
GIF ,*ppv %*name(CD,"%R","%1")
TXT ,*ppv %*name(CD,"%R","%1")
CFG ,*ppv %*name(CD,"%R","%1")
HOWM ,*ppv %*name(CD,"%R","%1")
}

KV_main	= {	; PPvメイン窓
UP	,%KC"@UP @N"
DOWN	,%KC"@DOWN @N"
LEFT	,%KC"@LEFT @N"
RIGHT	,%KC"@RIGHT @N"
SPACE    ,%KC"@SPACE @N"
\SPACE    ,%KC"@\SPACE @N"
}
```

## やり方

PPcでE_crに登録した拡張子にカーソルをあわせ、[Enter]でPPvを起動。PPvでカーソルを動かすと、アクティブなPPcのカーソルが連動し、対応したファイルを表示する。
