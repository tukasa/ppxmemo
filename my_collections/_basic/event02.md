---
title: EVENT
part: EVENT
date: 2023-01-19
last_modified_at: 
---
色々なイベントを捉え、特定の動作をさせることができる。


## FIRSTEVENT

起動時に一度実行する。

_PPxフォルダ内のkabegami.jpgを壁紙に_

```text
KC_main = {
FIRSTEVENT , *customize X_bg:Path=%0\kabegami.jpg
}
```

_PPxフォルダ内のDLLPATHフォルダにあるDLLを使用_

```text
KC_main = {
FIRSTEVENT , *set PATH+=%0\DLLPATH
}
```

_PPvを起動時最前面表示に_

```text
KV_main = {
FIRSTEVENT,*topmostwindow %N,1
}
```

## ACTIVEEVENT

アクティブになったときに実行する。

_2画面一体化型のペイン比率を一定に_

```text
KC_main = {
ACTIVEEVENT , *pairrate 70
}
```

## CLOSEEVENT

終了時に設定を保存したい場合や、フォーカスを戻したい場合に使う。

_PPv終了時にフォーカスをPPcに戻す_

```text
KV_main = {
CLOSEEVENT,*focus C
}
```

## LOADEVENT

壁紙や背景色を変更する場合に使う。

_Musicフォルダ以下にいる時はnagato.jpgに。それ以外の時はharuhi.jpgに_

```text
KC_main = {
LOADEVENT,*ifmatch "/D:\\Music/",%1 %: *customize X_bg:Path=%0\nagato.jpg %: *stop
 *customize X_bg:Path=%0\haruhi.jpg
}
```

_Musicフォルダ以下にいる場合は、背景色を青色に。それ以外の時は黒色に_

```text
KC_main = {
LOADEVENT,*ifmatch "/D:\\Music/",%1 %: *customize C_back=_BLU %: *stop
 *customize C_back=_BLA
}
```


## SELECTEVENT

連動ビューみたいなことを外部ソフトで行いたい場合に使う。

```text
KC_main = {
SELECTEVENT,%Obi D:\bin\MassiGra\MassiGra.exe %FCD %: *focus C
}
```
