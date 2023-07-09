---
title: 基本
part: 一行編集でランチャ
created_at: 2023-01-25
last_modified_at: 2023-07-10
---

![一行編集]({{ "/assets/images/launch01.png" | relative_url }})

一行編集には、任意の補完候補ファイルを読み込ませることができる。これを応用することで、一行編集をランチャとして活用することができる。

## 基本的な方法

一行ごとにコマンドあるいは実行パスを記載したlaunch.txtをPPxフォルダに作成する。

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
*string o,name=%*input("" -title:"PPlauncher" -mode:h -k:"*completelist /set /file:%%0launch.txt") %: *execute,%so"name"
```

## migemo

migemoを利用することもできる。その場合は、以下のコマンドになる。

```text
*string o,name=%*input("" -title:"PPlauncher" -mode:h -k:"*completelist /set /file:%%0launch.txt -match:6 ") %: *execute,%so"name"
```

