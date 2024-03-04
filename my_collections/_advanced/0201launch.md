---
title: コマンドの実行
part: 一行編集
created_at: 2023-01-25
last_modified_at: 2024-03-05
---

![一行編集]({{ "/assets/images/launch03.gif" | relative_url }})

## 行頭コメントとmigemo

一行編集に読み込ませる補完候補ファイルには、行頭コメントをつけることができる。

```text
;<comment>; text
```

これとmigemoを組み合わせることで、任意のコマンドを瞬時に実行することが可能になる。

## やり方

以下のようなファイルをPPxフォルダに作成する。

_launch.txt_
```text
git
	add .
	commit -m"%*input("" -title:"commit message")"
	push
	pull
	status
;<画像ビューア>; D:\bin\NeeView\NeeView.exe
;<EXIFに基づくリネーム>; D:\bin\rexifer\Rexifer.exe
*ppcust /edit ;編集して取込
*reboot ;Windows を再起動
*shutdown ;Windows をシャットダウン
;<Script実行>; *script %*input("%R" -title:"Scriptを実行" -mode:e -select:l)
;<ゴミ箱(dust)メニュー>; %z"#10:\",B
editor %0launch.txt ;編集
```

以下のコマンドを実行する。

```text
*string o,name=%*input("" -title:"PPlauncher" -mode:h -k:"*completelist -file:%%0launch.txt -match:6 ") %: *execute,%so"name"
```

