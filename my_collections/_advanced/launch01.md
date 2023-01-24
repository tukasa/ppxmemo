---
title: 補完候補リストの指定
part: 一行編集の活用
created_at: 2023-01-25
---

![一行編集]({{ "/assets/images/launch01.png" | relative_url }})

任意の補完候補リストを読み込ませて、一行編集を起動することができる。
一行ごとにコマンドあるいはパスを記載したlaunch.txtをPPxフォルダに作成しよう。

_launch.txt_
```text
git
	add .
	commit -m"%*input("" -title:"commit message")"
	push
	pull
	status
D:\bin
D:\data
D:\bin\NeeView\NeeView.exe
D:\bin\nyanfi\NyanFi.exe
*ppcust /edit ;編集して取込
*reboot ;Windows を再起動
*shutdown ;Windows をシャットダウン
editor %0launch.txt ;編集
```

以下を編集して取込。

```text
_Command = { ; ユーザコマンド・関数
ppl = *string o,name=%*input("" -title:"PPlauncher" -mode:h -k:"*completelist /set /file:%%0launch.txt") %:
 *ifmatch "o:e,a:d+",%so"name" %: *execute C,*jumppath "%so"name"" %: *stop
 *ifmatch "o:e,a:d-",%so"name" %: *execute ,"%so"name"" %: *stop
 *execute,%so"name"
}
```

3) PPTRAYW.EXEを実行、PPTrayを常駐させる。

## やり方

`*ppl`で、launch.txtを補完候補リストとした一行編集が表示される。入力内容により、

- フォルダ→PPcで開く
- それ以外→実行する

と分岐する。

