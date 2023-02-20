---
title: PPv中心の連動ビュー
part: PPv中心の連動ビュー
created_at: 2023-01-13
last_modified_at: 2023-02-21
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
PNG ,*ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
JPG ,*ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
JPEG ,*ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
BMP ,*ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
GIF ,*ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
TXT ,*ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
CFG ,*ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
HOWM ,*ppv %*name(CD,"%R","%1") -k *string i,ppcid=%%*rightstr("%n", 1)
}

KV_main	= {	; PPvメイン窓
UP	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@UP" %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@UP"
DOWN	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@DOWN" %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@DOWN"
LEFT	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@LEFT" %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@LEFT"
RIGHT	,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@RIGHT" %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@RIGHT"
SPACE    ,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@SPACE" %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@SPACE"
\SPACE    ,*ifmatch !0,0%si"ppcid" %: *execute C%si"ppcid",%%K"@\SPACE" %: *ppv -bootid:%*rightstr("%n", 1) -r %*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)") %: *stop
	%K"@\SPACE"
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

PPcでE_crに登録した拡張子にカーソルをあわせ、EnterでPPvを起動。PPvでカーソルを動かすと、起動元のPPcのカーソルが連動し、対応したファイルを表示する。
