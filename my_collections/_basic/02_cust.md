---
title: カスタマイズ用メニュー
tags: カスタマイズ
date: 2022-03-31
last_modified_at: 2022-03-31
---

PPxの初期化時、PPxフォルダにPPXDEF.CFGがあれば、それによる初期カスタマイズが自動で行われる。

PPXDEF.CFGをエディタで編集し、以下のカスタマイズ用メニューを末尾に追加しておくと、初期化しても使えて便利。

カスタマイズで色々なところをいじってて、状態を元に戻したいなと思ったら、F12を押してカスタマイズ用メニューを出し、初期化。 そして、CFGフォルダに行って、必要なCFGファイルをマーク。再びF12を押して、メニューから追加を選択。これで、元の状態に戻るわけだ。

{% raw %}
```text
-|M_Omake =
-|M_BgType =
-|M_cust =
M_cust    = { ** comment **
カスタマイザ(&C) = %K"@CUSTOMIZE"
編集して取込(&E) = %Ob *PPCUST /edit
-- =
取り込み(&1) = %Q"%FCを取り込みます"%:%Ob *PPCUST CS "%FCD"
追加(&2) = %Q"追加取込します"%:*customize @%FCD
-- =
PPX.CFGを取り込み(&3) = %Q"PPX.CFGを取り込みます"%:%Ob *PPCUST CS "%0\PPX.CFG"
PPX.CFGに書き出し(&4) = %Q"PPX.CFGに書き出します"%:%Ob *PPCUST CD "%0\PPX.CFG"
指定書き出し(&5) = %"指定ファイルに書き出します"%Ob *PPCUST CD %{%1\PPX-%*nowdatetime(y-N-D)%|.CFG%}
-- =
初期化(&I) =  %Q"初期化します"%:%Ob *PPCUST CINIT
-- =
壁紙の設定(&W) = %M_Omake
窓オプション(&O) = %K"@C_WIND"
-- =
アップデート(&U) = %Ob *checkupdate p
バージョン情報(&V) = %K"@ABOUT"
}

M_Omake    = {    ** comment **
壁紙を表示する位置(&T) = %M_BgType
壁紙を明るさ(&B) = *customize X_bg:Bright=%"明るさ(Bright)"%{%*getcust(X_bg:Bright)%}
壁紙を透明度(&O) = *customize X_bg:Opaque=%"透明度(Opaque)"%{%*getcust(X_bg:Opaque)%}
}

M_BgType    = {    ** comment **
しない = *customize X_bg:Type=0
左上 = *customize X_bg:Type=1
右上 = *customize X_bg:Type=3
デスクトップと同じ = *customize X_bg:Type=10
一体化窓内でつながるように調整 = *customize X_bg:Type=20
}

KC_main    = {    ; PPcメイン窓
F12    ,%M_cust,C
}
```
{% endraw %}
