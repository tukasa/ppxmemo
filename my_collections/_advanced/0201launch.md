---
title: 高度な指定
part: 一行編集
created_at: 2023-01-25
last_modified_at: 2023-08-19
---

![一行編集]({{ "/assets/images/launch01.png" | relative_url }})

一行編集でさらに高度なことを行いたいときには、`%*input`を使う。

## %*input

`%*input`を使うと、

- タイトル
- 編集するテキスト
- カーソル位置
- ダイアログ種類、ヒストリ種類、参照の動作

を指定することができる。以下はヘルプに載っている例。

```
{% raw %}*linemessage {%*input("text" -title:"Input title" -mode:g)}{% endraw %}
```

さらに、`-k:"command line" `または`-k command line `により、一行編集開始時に任意のコマンドを実行することができる。特に有用なのが`*completelist`だ。

## 補完候補ファイル

`*completelist`の`-file`オプションにより、一行編集に任意の補完候補ファイルを読み込ませることができる。
例えば以下のようなファイルをPPxフォルダに作成する。

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

以下のコマンドを実行すると、launch.txtを補完候補ファイルとして読み込んだ一行編集が起動する。

```text
*string o,name=%*input("" -title:"PPlauncher" -mode:h -k:"*completelist /set /file:%%0launch.txt") %: *execute,%so"name"
```

## migemo

`*completelist`の`-match`オプションにより、migemoを利用することができる。補完候補ファイルの行頭コメントと組み合わせると、その真価を発揮するだろう。

```text
*string o,name=%*input("" -title:"PPlauncher" -mode:h -k:"*completelist /set /file:%%0launch.txt -match:6 ") %: *execute,%so"name"
```

## 補完一覧の詳細な指定

`*completelist`の`-detail`オプションを使うと、補完一覧の内容を、その並び順も含め、より詳細に指定することができる。

```text
*string o,name=%*input("" -title:"PPlauncher" -mode:h -k:"*completelist /set /file:%%0launch.txt -match:6 -detail:""hist user"" ") %: *execute,%so"name"
```

