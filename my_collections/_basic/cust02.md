---
title: カスタマイズ用メニュー
part: カスタマイズ
created_at: 2022-03-31
last_modified_at: 2023-01-25
---

PPxの初期化時、PPxフォルダにPPXDEF.CFGがあれば、それによる初期カスタマイズが自動で行われる。

PPXDEF.CFGをエディタで編集し、以下のカスタマイズ用メニューを末尾に追加しておくと、初期化しても使えて便利。

カスタマイズで色々なところをいじってて、状態を元に戻したいなと思ったら、F12を押してカスタマイズ用メニューを出し、初期化。 そして、CFGフォルダに行って、必要なCFGファイルをマーク。再びF12を押して、メニューから追加を選択。これで、元の状態に戻るわけだ。

{% raw %}
```text
-|M_cust =
M_cust    = {
カスタマイザ(&C) = %K"@CUSTOMIZE"
編集して取込(&E) = %OB *PPCUST /edit
-- =
取り込み = %OB *PPCUST CS %FCD
追加 = %OB *customize @%FCD
-- =
PPX.CFGを取り込み = %OB *PPCUST CS %0\PPX.CFG
PPX.CFGに書き出し = %OB *PPCUST CD %0\PPX.CFG
指定書き出し = %OB *PPCUST CD %{%1\PPX-%*nowdatetime(y-N-D)%|.CFG%}
-- =
初期化(&I) =  *PPCUST CINIT
設定を一時保存して初期化 =  %OBs *PPCUST CD %0\QUICKSAVE.CFG %: *PPCUST CINIT
一時保存した設定に戻す(&R) =  %OBs *PPCUST CINIT %: *PPCUST CS %0\QUICKSAVE.CFG
-- =
アップデート(&U) = %OB *checkupdate p
バージョン情報(&V) = %K"@ABOUT"
}

KC_main    = {    ; PPcメイン窓
F12    ,%M_cust,C
}
```
{% endraw %}
