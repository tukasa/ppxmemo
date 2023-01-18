---
title: 少しあふっぽくする
part: ○○っぽくする
date: 2023-01-13
---

カーソルキーの動作や画像ビューといった基本的な箇所だけあふっぽくする。

![あふっぽいppx]({{ "/assets/images/ppoku01.png" | relative_url }})

以下を編集して取込。

```text
X_combo = 1 ; 複数 PPc を一体化 0:しない 1:する
X_mpane = 2,2 ; 一体化時の最大同時表示ペイン数,起動時のペイン数
X_inag = 0 ; 現在窓以外はグレー調に 0:しない 1:する
XC_page	= 1
XC_mvLR	= 4,1,0,B0100,0,B100	; [←][→]

_others	= {	; その他設定
SyncViewID	= Y
}
_Command	= {	; ユーザコマンド・関数
afxview	= *ifmatch %NC,%NCBA#L %: *ppv -bootid:Y -parent:%N~ %*name(CD,"%R","%1") -k *execute C,*ppvoption sync on %: *stop
	*ppv -bootid:A -popup:%NC# %*name(CD,"%R","%1")
allview	= *ppv -bootid:A -popup:%NC# %*name(CD,"%R","%1")
halfview	= *ppv -bootid:Y -parent:%N~ %*name(CD,"%R","%1") -k *execute C,*ppvoption sync on
}
E_cr	= {	; [Enter]用判別
TXT	,*allview
:UTEXT	,*allview
JPEG	,*afxview
:JPEG	,*afxview
BMP	,*afxview
:BMP	,*afxview
HOWM	,*allview
CFG	,*allview
INI	,*allview
PNG	,*afxview
:PNG	,*afxview
GIF	,*afxview
:GIF	,*afxview
}

KC_main	= {	; PPcメイン窓
TAB	,*ifmatch 0,0%NVY %: %K"@TAB" %: *stop
RIGHT	,*ifmatch 0,0%NVY %: %K"@RIGHT" %: *stop
	 %K"@DOWN"
LEFT	,*ifmatch 0,0%NVY %: %K"@LEFT" %: *stop
	 %K"@UP"
ENTER	,*ifmatch 0,0%NVY %: %K"@ENTER" %: *stop
	 %K"@\Y"
}
KV_main	= {	; PPvメイン窓
ENTER , %K"@Q" %: %KC"@DOWN"
ESC = @Q
}

KV_page = {
LEFT ,%K"@PUP"
RIGHT ,%K"@PDOWN"
}

KV_img = {
UP ,%KC"@UP@N"
LEFT ,%KC"@UP@N"
DOWN ,%KC"@DOWN@N"
RIGHT ,%KC"@DOWN@N"
SPACE    ,%KC"@SPACE@N"
\SPACE    ,%KC"@\SPACE@N"
}
```
