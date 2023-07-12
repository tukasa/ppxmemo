---
title: FIRSTEVENT
part: EVENT
created_at: 2023-01-19
last_modified_at: 2023-07-12
---
起動時に一度実行する。

- 設定項目にない初期設定を行う
- 条件に応じて初期設定を変更する
- ユーザデータやエイリアスの初期化

といった使い方がある。

## ポータブル運用時の初期設定

PPxをUSB等に入れて持ち歩いている場合、パスが環境によって変わるため、設定項目での設定ができない事態が生じる。これをFIRSTEVENTで解決する。

_PPxフォルダ内のkabegami.jpgを壁紙に_

```text
KC_main = {
FIRSTEVENT , *customize X_bg:Path=%0\kabegami.jpg
}
```

_PPxフォルダ内のDLLPATHフォルダにあるDLLを使用(ヘルプにある例)_

```text
KC_main = {
FIRSTEVENT , *set PATH+=%0\DLLPATH
}
```

## アップデートの確認

起動時にアップデートを確認する。以下はヘルプの例。

```text
KC_main = {
  FIRSTEVENT , *checkupdate ni
}
```

## PPtrayの起動

PPc起動時、PPtrayが起動してなければ起動させる。

```text
KC_main = {
FIRSTEVENT , *ifmatch 0,0%NTRA %: *pptray
}
```

## Everythingの無効化

Everything Moduleを入れていると、一行編集の動作が重くなってしまうので、これを抑制する。

```text
K_lied	= {
FIRSTEVENT	,*completelist -module:off
}
```
