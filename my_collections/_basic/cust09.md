---
title: 隠しメニュー
part: 基本的なカスタマイズ
created_at: 2022-03-31
last_modified_at: 2023-01-24
---
PPc下部にある情報行に注目しよう。情報行にマウスカーソルをあわせると

![PPc隠しメニュー]({{ "/assets/images/kakushimenu01.gif" | relative_url }})

このように隠し項目が表示される。これが隠しメニューだ。現れた各項目をクリックすると、何らかのコマンドを実行する。

同様の隠しメニューは、PPvにも存在する。

![PPv隠しメニュー]({{ "/assets/images/kakushimenu02.png" | relative_url }})

## GUIによるカスタマイズ

ボタンタブを開き、種類からHM_ppcを選択すればいい。PPvの場合はHM_ppvだ。

![カスタマイザー]({{ "/assets/images/kakushimenu03.png" | relative_url }})

①が表示名で、②が実行するコマンド。①の右にある「文字色」と「背景色」で、色を変更する。項目の設定が終わったら、忘れずに「設定」を押そう。

新しい項目を追加したい場合は、右上から新規を選択。不要な項目は「削除」で削除する。

## テキスト編集によるカスタマイズ

HM_ppcを編集することにより、PPcの隠しメニューを。HM_ppvを編集することにより、PPvの隠しメニューをカスタマイズすることができる。
PPcの隠しメニューは二段表示だ。HM_ppcの前半部の項目が上段、後半部の項目が下段に対応している。PPcの隠しメニューを変更する場合は、位置関係を気にしながらHM_ppc全体を編集した上で、取込動作をするといいだろう。

![PPcの隠しメニュー]({{ "/assets/images/kakushimenu04.png" | relative_url }})

```text
HM_ppc	= {	; PPc(前半が上段、後半が下段
Root	, _CYA,_AUTO = @'\'
allM	, _AUTO,_AUTO = @HOME
Driv	, _AUTO,_AUTO = @\L
Copy	, _AUTO,_AUTO = @C
Edit	, _AUTO,_AUTO = E
Pack	, _AUTO,_AUTO = P
Ren	, _AUTO,_AUTO = @R
Sort	, _AUTO,_AUTO = @S
MkDr	, _AUTO,_AUTO = @K
Tree	, _AUTO,_AUTO = @\T
Exec	, _AUTO,_AUTO = @X
Shel	, _AUTO,_AUTO = @H
Up	, _CYA,_AUTO = @BS
revM	, _AUTO,_AUTO = @\HOME
Pjmp	, _AUTO,_AUTO = @0
Move	, _AUTO,_AUTO = @M
View	, _AUTO,_AUTO = @N
Unpk	, _AUTO,_AUTO = @U
Del	, _AUTO,_AUTO = @D
Writ	, _AUTO,_AUTO = @W
Wid	, _AUTO,_AUTO = @';'
Attr	, _AUTO,_AUTO = @A
Find	, _AUTO,_AUTO = @F
}
```

PPvの隠しメニューは一段表示になっている。

![PPvの隠しメニュー]({{ "/assets/images/kakushimenu05.png" | relative_url }})

```text
HM_ppv	= {	; PPv
disp	, _AUTO,_AUTO = @':'
code	, _AUTO,_AUTO = @'@'
Find	, _AUTO,_DBLU = @F
F ^	, _AUTO,_DBLU = @'['
F v	, _AUTO,_DBLU = @']'
}
```

ちなみに、表示する文字には、４文字のアルファベットの他にも、２文字の漢字を利用することができる。

![漢字の隠しメニュー]({{ "/assets/images/kakushimenu06.png" | relative_url }})
