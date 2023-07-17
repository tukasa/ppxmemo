---
title: SELECTEVENT
part: EVENT
created_at: 2023-01-19
last_modified_at: 2023-07-17
---
カーソル移動にあわせた連携処理に使用する。

- PPvによる連動ビュー
- 連動プロパティ表示
- ファイルの詳細情報の連動
- 連動パス・表示パス同期

についてはデフォルトでできるので、これ以外の特殊な連動をPPx内で行うか、あるいは外部アプリケーションとの連動に使うか、ということになるだろう。
前者の例としては、[反対窓にフォルダ内容を表示]({{ "/advanced/mode04" | relative_url }})や[DockShow]({{ "/basic/module04" | relative_url }})を参考にしてほしい。

_MassiGraとの連動_

```text
KC_main = {
SELECTEVENT,*ifmatch .JPG;.PNG %: %Obi D:\bin\MassiGra\MassiGra.exe %FCD %: *focus C
}
```

_MPC HCとの連動_

```text
KC_main = {
SELECTEVENT,*ifmatch .mp4 %: mpc %FCD /nofocus
}
```

## コマンドでオン・オフ切り替え

大抵の場合、SELECTEVENTは必要なときに一時的に使うことになるだろう。
以下のコマンドで、SELECTEVENTのオン・オフをトグルで切り替えることができる。

```text
*linecust ^mpc,KC_main:SELECTEVENT,*ifmatch .mp4 %%: mpc /nofocus %%FCD %: %K"loadcust"
```

## [ESC]で終了

[ESC]でSELECTEVENTを終了させたい場合は、次のようにする。
以下を編集して取込。

```text
K_selectevent    = {
ESC    ,*mapkey delete,K_selectevent %: *linecust mpc,KC_main:SELECTEVENT, %: *linemessage SELECTEVENT END
}
```

以下のコマンドを実行。

```text
*mapkey use,K_selectevent %: *linecust mpc,KC_main:SELECTEVENT,*ifmatch .mp4 %%: mpc  /nofocus %%FCD %: %K"loadcust"
```
