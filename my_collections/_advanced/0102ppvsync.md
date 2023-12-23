---
title: 一対一対応
part: PPv中心の連動ビュー
created_at: 2023-01-13
last_modified_at: 2023-08-19
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
UP	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@UP" %: *cd %0 %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@UP"
DOWN	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@DOWN" %: *cd %0 %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@DOWN"
LEFT	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@LEFT" %: *cd %0 %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@LEFT"
RIGHT	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@RIGHT" %: *cd %0 %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@RIGHT"
SPACE	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@SPACE" %: *cd %0 %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@SPACE"
\SPACE	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@\SPACE" %: *cd %0 %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@\SPACE"
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
