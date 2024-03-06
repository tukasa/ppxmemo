---
title: ファイル判別の追加
part: ファイル判別
created_at: 2022-03-31
last_modified_at: 2023-07-22
---
デフォルトでは

- Enter
- Shift＋Enter
- Ctrl+Enter

のファイル判別が用意されている。ここでは、Enterのファイル判別をカスタマイズしてみよう。

## GUIによるカスタマイズ

- カスタマイザー - ファイル判別タブ

から PPc [Enter] /E_cr を選択する。

![E_cr]({{ "/assets/images/hanbetu01.png" | relative_url }})

判別名に拡張子を。登録内容詳細に実行したいコマンドを入力して、設定を押す。

![設定ボタンを押す]({{ "/assets/images/hanbetu02.png" | relative_url }})

設定が終わったら、適用あるいはOKを押す。

## テキスト編集によるカスタマイズ

- 判別方法,コマンド

という書式で記載する。

```text
E_cr	= {	; [Enter]用判別
TXT	,editor %FCD
}
```
