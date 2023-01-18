---
title: PPv中心の連動ビュー
part: PPv中心の連動ビュー
date: 2023-01-13
last_modified_at: 2023-01-19
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
PNG ,*ppv %*name(CD,"%R","%1") -k *mapkey use,K_syncppv %%: *string i,ppcid=%%*rightstr("%n", 1)
JPG ,*ppv %*name(CD,"%R","%1") -k *mapkey use,K_syncppv %%: *string i,ppcid=%%*rightstr("%n", 1)
JPEG ,*ppv %*name(CD,"%R","%1") -k *mapkey use,K_syncppv %%: *string i,ppcid=%%*rightstr("%n", 1)
BMP ,*ppv %*name(CD,"%R","%1") -k *mapkey use,K_syncppv %%: *string i,ppcid=%%*rightstr("%n", 1)
GIF ,*ppv %*name(CD,"%R","%1") -k *mapkey use,K_syncppv %%: *string i,ppcid=%%*rightstr("%n", 1)
TXT ,*ppv %*name(CD,"%R","%1") -k *mapkey use,K_syncppv %%: *string i,ppcid=%%*rightstr("%n", 1)
}

K_syncppv	= {
UP	,*execute C%si"ppcid",%%K"@UP" %: %v%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
DOWN	,*execute C%si"ppcid",%%K"@DOWN" % %v%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
LEFT	,*execute C%si"ppcid",%%K"@LEFT" % %v%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
RIGHT	,*execute C%si"ppcid",%%K"@RIGHT" % %v%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
SPACE    ,*execute C%si"ppcid",%%K"@SPACE" % %v%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
\SPACE    ,*execute C%si"ppcid",%%K"@\SPACE" % %v%*extract(C%si"ppcid""%(%*name(CD,"%R","%1")%)")
}
```

## やり方

PPcでE_crに登録した拡張子にカーソルをあわせ、EnterでPPvを起動。PPvでカーソルを動かすと、起動元のPPcのカーソルが連動し、対応したファイルを表示する。
