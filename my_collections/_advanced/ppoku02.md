---
title: できるだけあふっぽくする
part: ○○っぽくする
date: 2023-01-13
---

できるだけあふっぽくする。
ログ窓がほしいときはメニューバーの「view - レイアウト - ログ」で表示できる。

![ppxとあふ]({{ "/assets/images/ppoku02.png" | relative_url }})

以下を編集して取込。

```text
XC_celD	= _AUTO,_AUTO,1,7	; エントリ表示 文字,背景,カーソル,マーク
XC_dpmk	= 1	; エントリマスクを表示	0:しない 1:する
X_combo = 1 ; 複数 PPc を一体化 0:しない 1:する
X_mpane = 2,2 ; 一体化時の最大同時表示ペイン数,起動時のペイン数
X_inag = 0 ; 現在窓以外はグレー調に 0:しない 1:する
XC_page	= 1
XC_mvLR	= 4,1,0,B0100,0,B100	; [←][→]
CC_log	= _WHI,_BLA	; 共用ログ、アドレスバー(文字,背景)_AUTO可
XV_drag = 2,1,3,0 ; ドラッグ開始ボタン スクロール,選択,窓移動,ジェスチャ(右のみ)
  ; 0:使用しない 1:左 2:右 3:中/ホイール 4:左右同時 5:第4 6:第5
X_fles	= 1	; 画面のちらつき対策を 0:しない 1:する
XC_isea	= 0,1,1,0,0	; インクリメンタルサーチ動作 方法,位置,対象,ハイライト,ヒストリ保存
C_eInfo	= _AUTO,_DRED,_AUTO,_DBLA,_DBLU,_DCYA, _DBLA,_BRO,_GRE,_WHI,_AUTO,HA00000,_AUTO, _SBLU,_BRO,_CYA,_GRE,_RED,_MAG,_DRED, _AUTO 
X_bg	= { 
Bright	= 60
}

_others	= {	; その他設定
SyncViewID	= Y
}

_Command	= {	; ユーザコマンド・関数
afxview	= *ifmatch %NC,%NCBA#L %: *ppv -bootid:Y -parent:%N~ %*name(CD,"%R","%1") -k *execute C,*ppvoption sync on %: *stop
	*ppv -bootid:A -popup:%NC# %*name(CD,"%R","%1")
allview	= *ppv -bootid:A -popup:%NC# %*name(CD,"%R","%1")
halfview	= *ppv -bootid:Y -parent:%N~ %*name(CD,"%R","%1") -k *execute C,*ppvoption sync on
}

KC_main = { ; PPcメイン窓
TAB	,*ifmatch 0,0%NVY %: %K"@TAB" %: *stop
ENTER	,*ifmatch 0,0%NVY %: %K"@ENTER" %: *stop
	 %K"@\Y"
ESC	,*ifmatch 0,0%NVY %: %K"@PAUSE" %: *stop
	 *execute CA,*ppvoption sync off %: *focus CAEND = @F5
HOME = @\HOME
LEFT	,*ifmatch 0,0%NVY %: %K"@LEFT" %: *stop
	 %K"@UP"
RIGHT	,*ifmatch 0,0%NVY %: %K"@RIGHT" %: *stop
	 %K"@DOWN"
INS = @\INS
DEL = @\DEL
'-'	= @^D
NUM- ,*pairrate 50
A = @\HOME
D = @\D
E ,%"JMTE|Text edit"%Ob,editor %*name(CD,"%R","%1")
F = @\J
H = @^\LEFT
I ,*countsize
J = @0
L = @\L
N , %j%*tree(\\)
O	,*ifmatch "/^%*regexp("%FD","s/\\/\\\\/g")$/",%2 %: %J%*extract(~"%%R") %: *stop
	 %j%2
Q = @&F4
T , %j%*tree(%1)
W = @O
Z = CUSTOMIZE
':' = @F
'*' = @\F
'`' = @'+'
'\' = NULL
V_HDC , %J\
V_HE2 , %KC"^\F10
\END , %K~"@F5
\HOME = @\END
\A = @\END
\C , *ppcfile !copy,%M_pjump,A
\D = @D
\E ,*makefile %1\%"新規テキストの編集"%$E.txt %: %Ob editor %1\%"新規テキストの編集"%$E.txt
\F = @^W
\J = @L
\M ,*ppcfile !move,%M_pjump,A
\O	,*ifmatch "/^%*regexp("%FD","s/\\/\\\\/g")$/",%2 %: *execute ~,%%J%R %: *stop
	 *execute ~,%%j%1
\P , *pack "%2",indiv
\V = @I
\X = @H
^ENTER = @Z
^SPACE ,*range lastmark cursor
^END = @^F5
^LEFT ,*cursor 8,1,12,0,12,0
^UP = @PUP
^RIGHT ,*cursor 8,1,13,0,13,0
^DOWN = @PDOWN
^INS ,%z"#17:\"
^DEL ,%z"#10:\"
^V_HBA ,*cursor 16,1,5,1,5,0
^\END ,%K"@^F5"
^\LEFT = @^LEFT
^\UP = @DEL @UP @UP @INS @DOWN
^\RIGHT = @^RIGHT
^\DOWN = @DEL @INS @DOWN
^\V_HBA ,*cursor 16,-1,5,1,5,0
&ENTER , *ifmatch 0,0%NVY %: *stop
	 %K"@\Y" %: %Oi *ppv -bootid:A -popup:%NC# %*name(CD,"%R","%1") %: *maximize %NVA
&RIGHT ,*ifmatch %NC,%NCBA#L %: *pairrate +3 %: *stop
 *pairrate -3
&LEFT ,*ifmatch %NC,%NCBA#L %: *pairrate -3 %: *stop
 *pairrate +3
&Z ,*ppc -alone
&'\' ,%M_ClipPath
&\Z ,*ppc -runas -alone
^A = @&\A
^B = @&\B
^C = @&\C
^D = @&\D
^E = @&\E
^F = @&\F
^G = @&\G
^H = @&\H
^I = @&\I
^J = @&\J
^K = @&\K
^L = @&\L
^M = @&\M
^N = @&\N
^O = @&\O
^P = @&\P
^Q = @&\Q
^R = @&\R
^S = @&\S
^T = @&\T
^U = @&\U
^V = @&\V
^W = @&\W
^X = @&\X
^Y = @&\Y
^Z = @&\Z
^V_H31 = @&\1
^V_H32 = @&\2
^V_H33 = @&\3
^V_H34 = @&\4
^V_H35 = @&\5
^V_H36 = @&\6
^V_H37 = @&\7
^V_H38 = @&\8
^V_H39 = @&\9
}

KV_main = {
ENTER , %K"@Q" %: %KC"@DOWN"
ESC = @Q
2 , *viewoption -tab:2
4 , *viewoption -tab:4
8 , *viewoption -tab:8
\E , *viewoption -euc
\I , *viewoption -utf16be
\J , *viewoption -jis
\O , *viewoption -utf8
\S , *viewoption -sjis
\U , *viewoption -utf16
&Z , *ppc -alone
&\Z , *ppc -runas -alone
}

KV_crt = {
SPACE = @']'
E , %Ob editor %FCD %: %K"@Q"
H = @'['
L = @']'
F1 = @HOME
F2 = @END
F3 = @J
F4 = @F
F5 = @']'
\ENTER , %Ob editor %FCD %: %K"@Q"
\SPACE = @'['
\C = @C
\F = @B
\L = @'['
\N = @T
\T = @C
\F4 = @B
\F5 = @'['
^SPACE = @I
^PUP = @HOME
\PDOWN = @END
&UP , %KC"@UP@N"
&DOWN , %KC"@DOWN@N"
}

KV_page = {
SPACE = @']'
LEFT = @PUP
RIGHT = @PDOWN
E , %Ob editor %FCD %: %K"@Q"
H = @'['
L = @']'
F1 = @HOME
F2 = @END
F3 = @J
F4 = @F
F5 = @']'
\ENTER , %Ob editor %FCD %: %K"@Q"
\SPACE = @'['
\C = @C
\F = @B
\L = @'['
\N = @T
\T = @C
\F4 = @B
\F5 = @'['
^SPACE = @I
^PUP = @HOME
\PDOWN = @END
&UP , %KC"@UP@N"
&DOWN , %KC"@DOWN@N"
}

KV_img    = {
SPACE , %KC"@SPACE@N"
END , *zoom -1
HOME , *zoom 0
LEFT ,%KC"@UP@N"
UP ,%KC"@UP@N"
RIGHT ,%KC"@DOWN@N"
DOWN ,%KC"@DOWN@N"
G = @Q
L = @K
R = @L
'\' ,%M_WallPaper
\SPACE , %KC"@\SPACE@N"
\END , *zoom -1
^I , *cliptext %R
^W , *setcust X_bg:P_%*extract(C"%%n")=%FCD %: *customize X_bg:T_%*extract(C"%%n")=1
&ENTER , *togglewinsize
}

E_cr	= {	; [Enter]用判別
*	,*allview
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

-|M_ClipPath =

M_ClipPath    = {
ファイル名\t【カーソル上】    = *cliptext %R %: *linemessage Clip : %R
フルパスファイル名\t【カーソル上】    = *cliptext %FCD %: *linemessage Clip : %FCD
--    = 
フルパス名    = *cliptext %1 %: *linemessage Clip : %1
--    = 
ファイル名\t【マーク・スペース区切り】    = *cliptext %#FC %: *linemessage Clip : %#FC
フルパスファイル名\t【マーク・スペース区切り】    = *cliptext %#FCD %: *linemessage Clip : %#FCD
}

-|M_WallPaper =

M_WallPaper = { ** comment **
画像をクリップボードに転送 = %K"@^C"
情報をクリップボードに転送 = *cliptext %R 
ファイルに保存する = %K"@^S"
-- =
PPC[&A]の壁紙にする = *setcust X_bg:P_ca=%FCD %: *customize X_bg:T_ca=1
PPC[&B]の壁紙にする = *setcust X_bg:P_cb=%FCD %: *customize X_bg:T_cb=1
-- =
PPC[A]の壁紙をナシにする = *setcust X_bg:-|P_ca= %: *customize X_bg:-|T_ca=
PPC[B]の壁紙をナシにする = *setcust X_bg:-|P_cb= %: *customize X_bg:-|T_cb=
}
```
