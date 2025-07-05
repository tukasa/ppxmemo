---
title: 一対一対応
part: PPv中心の連動ビュー
created_at: 2023-01-13
last_modified_at: 2024-10-04
---

複数のPPcを開いている際、基本編だと意図しない動作になることがある。そこで、PPcとPPvを一対一対応させ、以下のように動作させる。

- PPvでのカーソル動作と起動元PPcを連動
- PPvを閉じた際に起動元PPcにフォーカス
- キャレットモード時は連動させない

![ppvの連動ビュー一対一対応]({{ "/assets/images/ppvsync02.png" | relative_url }})

## 準備

以下を編集して取込。

```text
_Command	= {	; ユーザコマンド・関数
myppv	= *ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
}

E_cr = { ; [Enter]用判別
:JPEG ,
:BMP ,
:XJS ,
:XVBS ,
PNG ,*myppv
JPG ,*myppv
JPEG ,*myppv
BMP ,*myppv
GIF ,*myppv
TXT ,*myppv
CFG ,*myppv
HOWM ,*myppv
}

KV_main	= {	; PPvメイン窓
UP	,*ifmatch 0,0%si"ppcid" %: %K"@UP" %: *stop
	*execute C%si"ppcid",%%K"@UP"
	%J%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
DOWN	,*ifmatch 0,0%si"ppcid" %: %K"@DOWN" %: *stop
	*execute C%si"ppcid",%%K"@DOWN"
	%J%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
LEFT	,*ifmatch 0,0%si"ppcid" %: %K"@LEFT" %: *stop
	*execute C%si"ppcid",%%K"@LEFT"
	%J%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
RIGHT	,*ifmatch 0,0%si"ppcid" %: %K"@RIGHT" %: *stop
	*execute C%si"ppcid",%%K"@RIGHT"
	%J%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
SPACE	,*ifmatch 0,0%si"ppcid" %: %K"@SPACE" %: *stop
	*execute C%si"ppcid",%%K"@SPACE"
	%J%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
\SPACE	,*ifmatch 0,0%si"ppcid" %: %K"@\SPACE" %: *stop
	*execute C%si"ppcid",%%K"@\SPACE"
	%J%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
ENTER	= @Q
CLOSEEVENT    ,*ifmatch !0,0%si"ppcid" %: *focus C%si"ppcid" %: *stop
}

KV_crt	= {	; PPvテキスト(キャレット)追加設定
UP	,%K"@UP"
DOWN	,%K"@DOWN"
LEFT	,%K"@LEFT"
RIGHT	,%K"@RIGHT"
SPACE    ,%K"@SPACE"
\SPACE    ,%K"@\SPACE"
}
```

## やり方

PPcでE_crに登録した拡張子にカーソルをあわせ、[Enter]でPPvを起動。PPvでカーソルを動かすと、起動元のPPcのカーソルが連動し、対応したファイルを表示する。
