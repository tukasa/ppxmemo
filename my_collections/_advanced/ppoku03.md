---
title: 少しだいなっぽくする
part: ○○っぽくする
created_at: 2023-01-13
---

![dynaっぽいPPx]({{ "/assets/images/dyna01.png" | relative_url }})

```text
{% raw %}
 MC_celS = { ; エントリ表示 書式([;]メニュー)
だいな1 = M wF16,5 Z10 S1 T14 s1
だいな2 = M wF16,5 z10 S1 T14 s1
だいな3 = M wF16,5 zK10 S1 T14 s1
}
KC_main = { ; PPcメイン窓
B ,%"Binary menu" %M_bin
E ,%"JMTE|Text edit"%Orib,editor %FDC
I ,*ifmatch "option:e,attribure:d+" %: *countsize
L = @\L
N ,*makefile %${%1\%|%} %: %Ob notepad.exe %${%1\%|%}
P ,*pack "%2%\|%X|" %Or-
W = @F12
V ,*ppv -hex -popup:%NC# %FDC
F4 = @D
F6 = @S
F7 = @F
F9 = @\L
F10 = @U
F11 ,*maximize %NC#
F12 ,*shownormal %NC#
ESC = @&F4
HOME = @\HOME
'@' ,%z
9 ,%j#18:\
LEFT ,*cursor 4, -1,6,B0100,6,B0100
RIGHT ,*cursor 4, 1,6,B0100,6,B0100
\ENTER = @Z
',' ,*RotateExecute dynastyle,*viewstyle だいな1,*viewstyle だいな2,*viewstyle だいな3
'~' ,*ifmatch "option:e,attribure:d+" %: *execute ~,*jumppath %FCD
\F1 = @A
\F2 = @I
\F3 = @M
\F8 ,%"JMTE|Text edit"%Orib,editor %FDC
\F9 ,*ppv -hex -popup:%NC# %FDC
\F10 ,*pack "%2%\|%X|" %Or-
\HOME ,*unmarkentry
\RIGHT ,*cursor 8,1,13,0,13,0
\LEFT ,*cursor 8,1,12,0,12,0
\DOWN = @PDOWN
\UP = @PUP
^D ,*cursor 4, 1,6,B0100,6,B0100
^E = @UP
^F = @J
^M = @'+'
^S ,*cursor 4, -1,6,B0100,6,B0100
^X = @DOWN
^RIGHT ,*pairrate +1
^LEFT ,*pairrate -1
^DOWN ,*pairrate 50
^\RIGHT = @^RIGHT
^\LEFT = @^LEFT
}
KV_main = { ; PPvメイン窓
ENTER ,%K"@Q" %: %KC"@DOWN"
SPACE ,%KC#C"@DOWN@N"
BS ,%KC#C"@UP@N"
F11 ,*maximize %NC#
F12 ,*shownormal %NC#
}
KV_page = { ; PPvテキスト(ページ)追加設定
B ,%K"@["
E ,%"JMTE|Text edit"%Orib,editor %FDC
I ,%K"@U"
L ,%K"@]"
T = @TAB
V ,%K"@C"
W ,%K"@;"
F3 = @']'
TAB ,*RotateExecute tbmode,*viewoption -hex,*viewoption -text
HOME ,%K"@^HOME"
\HOME ,%K"@^END"
\UP = @PUP
\DOWN = @PDOWN
^INS = @^C
}
KV_crt = { ; PPvテキスト(キャレット)追加設定
B ,%K"@["
E ,%"JMTE|Text edit"%Orib,editor %FDC
I ,%K"@U"
L ,%K"@]"
T = @TAB
V ,%K"@C"
W ,%K"@;"
F3 = @']'
TAB ,*RotateExecute tbmode,*viewoption -hex,*viewoption -text
HOME ,%K"@^HOME"
\HOME ,%K"@^END"
\UP = @PUP
\DOWN = @PDOWN
^INS = @^C
}

E_cr = { ; [Enter]用判別
PNG ,*ppv -popup:%NC# %FDC
:JPEG ,*ppv -popup:%NC# %FDC
JPEG ,*ppv -popup:%NC# %FDC
JPG ,*ppv -popup:%NC# %FDC
:BMP ,*ppv -popup:%NC# %FDC
BMP ,*ppv -popup:%NC# %FDC
GIF ,*ppv -popup:%NC# %FDC
TXT ,*ppv -popup:%NC# %FDC
INI ,*ppv -popup:%NC# %FDC
CFG ,*ppv -popup:%NC# %FDC
}

KV_img = { ; PPv画像追加設定
R ,%K-C"@R"
X = @L
Z = @K
HOME ,*RotateExecute id,*zoom 0,*zoom -1
}

-|MC_menu =
-|M_menuCFile =
-|M_menuCEdit =
-|M_menuCTool=
-|M_menuCWindow =
-|M_menuCHelp =

MC_menu = { ; PPc メニューバー、※指定すると初期メニューがなくなる
ファイル(&F) = %M_menuCFile
編集(&E) = %M_menuCEdit
ツール(&T) = %M_menuCTool
ウィンドウ(&W) = %M_menuCWindow
オプション(&O) = %K"CUSTOMIZE"
ヘルプ(&H) = %M_menuCHelp
}
M_menuCFile = { ** comment **
ドライブ情報...\t = %K"@I"
ドライブ移動(&W)...\t = %K"@\L"
ディレクトリサイズ\t = *countsize
}
M_menuCEdit = { ** comment **
すべて選択...\tK = *markentry
選択解除(&W)...\tShift+K = *unmarkentry
比較マーク\t = %K"@\O"
検索マーク\t = %K"@+"
壁紙に設定\t = 
機能一覧から\t = 
}
M_menuCTool = { ** comment **
ネットワークドライブの割当...\t = %K"NETUSE"
ネットワークドライブの切断(&W)...\t = %K"NETUNUSE"
ファイル検索\t = %K"@^W"
}
M_menuCWindow = { ** comment **
左右を均等にする...\tK = *pairrate 50
壁紙の更新(&W)...\tShift+K = 
}
M_menuCHelp = { ** comment **
目次...\tK = *help
about...\tShift+K = %K"ABOUT"
}

XC_stat = _AUTO,_AUTO,0,0,O"_GRE" R60 C / i"Marked" mn i"/" E0 S1 ms8 S1 i"Bytes" Df8 S1 i"Free" ; ステータス行
X_win = { ; 表示形式全般 *layout
CA = B001001001
CB = B001001001
}
F_mes = -16,0,0,0,400,0,0,0,128,3,2,1,17,ＭＳ 明朝 ; 汎用
C_entry = _WHI,_WHI,_CYA,_RED,_CYA, _MAG,_BLU,_GRE,_DWHI, _SBLU,_DBRO,_GRE,_RED,_MAG 
C_eInfo = _AUTO,_DRED,_AUTO,_DBLA,_DBLU,_DCYA,_DBLA,_BRO,_WHI,_WHI,_AUTO,_BLU,_AUTO, H404000,_BRO,_CYA,_GRE 
XC_celD = _AUTO,_AUTO,4,7 ; エントリ表示 文字,背景,カーソル,マーク 
X_inag = 0 ; 現在窓以外はグレー調に 0:しない 1:する
X_combo = 1 ; 複数 PPc を一体化 0:しない 1:する
X_combos = B0000000000001000010010000000000,B000 ; 一体化時の表示形式CC_log = _WHI,_BLA ; 共用ログ、アドレスバー(文字,背景)_AUTO可
X_mpane = 2,2 ; 一体化時の最大同時表示ペイン数,起動時のペイン数
XV_drag = 0,1,3,0 ; ドラッグ開始ボタン スクロール,選択,窓移動,ジェスチャ(右のみ)
  ; 0:使用しない 1:左 2:右 3:中/ホイール 4:左右同時 5:第4 6:第5
XC_dset = { 
* = B0000,0,0,0,-1,-1,B011111,B00000000000000000000000001,disp:"だいな1"
}
{% endraw %}
```