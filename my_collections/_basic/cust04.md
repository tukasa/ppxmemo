---
title: キー割り当て
part: 基本的なカスタマイズ
created_at: 2022-03-31
last_modified_at: 2023-07-22
---

## GUIによるカスタマイズ

### 種類の選択

![alt]({{ "/assets/images/key01.png" | relative_url }})

まずは、種類を選択。ファイラ部分のキーカスタマイズをしたいならPPc /KC_mainを選択しよう。他にいじる機会が多いのは、ビューア部分のPPV / KV_main。

### 新規を選択

![alt]({{ "/assets/images/key02.png" | relative_url }})

右上のウィンドウの、新規にカーソルあわせる。既に設定したキーバインドを変更したい場合は、それを選択しよう。

### キー指定

![alt]({{ "/assets/images/key03.png" | relative_url }})

キー指定をクリックし、割り当てたいキーを押して、Okをクリック。

### 内容を登録する

ついで、内容を登録する。登録内容詳細に直接書いてもいいし、

![alt]({{ "/assets/images/key04.png" | relative_url }})

右上のドロップダウンメニューから選択して、登録内容詳細を変更してもいいし、

![alt]({{ "/assets/images/key05.png" | relative_url }})

コマンド一覧をクリックするとポップアップするメニューから選択して、登録内容詳細を変更してもいい。 

![alt]({{ "/assets/images/key06.png" | relative_url }})

その後、設定ボタンを押す。これで、そのキーバインドが追加される。適用ボタンを押すと、その設定が反映される。

## テキスト編集によるカスタマイズ

- キー割り当ての対象
- 割り当て先キー名称
- 割り当てるキー名称/実行するコマンド

を以下の書式で記述する。

```text
KC_main	= {	; PPcメイン窓
^\T	= @F1
F9	,echo hoge
F10	,*string o,hoge=%FCD
	echo %so"hoge"
F11	,*ifmatch 0,"0%2" %: *linemessage 反対窓はありません %: *stop
	*linemessage 反対窓があります
FIRSTEVENT , *checkupdate ni
}
```

- 単純にキーを割り当てたい場合は「=」を、それ以外の場合は「,」を使う
- `^\T	= @F1`の「@」は、初期割り当てキーを指定するためのもの。これがないと、[F1]をカスタマイズしていた場合、その内容を読み取ってしまう
- 実行したいキーには、各種EVENTを登録することもできる

