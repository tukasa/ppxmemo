---
title: LOADEVENT
part: EVENT
created_at: 2023-01-19
last_modified_at: 2023-07-12
---
ディレクトリの読み込みが完了したときに使用する。以下の用途がある。

- パスに応じて壁紙や背景色を変更する
- パスを履歴に追加する
- スクリプトを実行する
- [保存したマーク・ハイライトを再現する]({{ "/advanced/mode01" | relative_url }})

*diroptionを使うほうが適切な場合もあるので、それも考慮してほしい。

_パスに応じて壁紙を変更_

```text
KC_main = {
LOADEVENT,*ifmatch "/D:\\Music/",%1 %: *customize X_bg:Path=%0\tukasa.jpg %: *stop
 *customize X_bg:Path=%0\kagami.jpg
}
```

_パスに応じて背景色を変更_

```text
KC_main = {
LOADEVENT,*ifmatch "/D:\\Music/",%1 %: *customize C_back=_BLU %: *stop
 *customize C_back=_BLA
}
```

_パスを履歴に追加_

```text
KC_main = {
LOADEVENT,*addhistory u,"%1"
}
```
