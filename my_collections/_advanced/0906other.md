---
title: 特定ディレクトリの背景色や壁紙を変更
part: その他
created_at: 2024-03-06
last_modified_at: 
---

![背景色や背景画像を変更]({{ "/assets/images/bgchange01.gif" | relative_url }})

## 事前準備

まずは、通常時の背景画像と背景色を設定する。以下のコマンドを適当なディレクトリで一度実行する。これは背景色も背景画像もなしの設定。

```text
*diroption -"*" cmd:"*deletecust X_bg:P_%%n %%: *deletecust X_bg:T_%%n %%: *color back"
```

## 特定のディレクトリ以下の背景色を変更

該当ディレクトリへ行き、以下のコマンドを実行する。

```
*diroption -thisbranch cmd "*color back %"_DBLA: 暗灰  _DBLU: 暗青  _DRED: 暗赤/茶  _DMAG: 暗紫 _DGRE: 暗緑  _DCYA: 暗水  _DBRO: 暗黄"%{_DBLU%}"
```

## 特定のディレクトリ以下の背景画像を変更

以下を編集して取込。

```
_Command	= {	; ユーザコマンド・関数
opensubwin	= *ppc -r -bootid:x -single -k *jumppath %*arg(1) %%: *fitwindow %NC,%%NC,20 %%: *mapkey use,K_subwin %%: *js "PPx.EntryIndex = 2" %%: *linemessage %*arg(2)
}

K_subwin	= {	** comment **
\ENTER	,*execute ,%*getcust(_User:temp_exec)
}
```

該当ディレクトリに行き、以下のコマンドを実行する。

```
*setcust _User:temp_exec=*execute %n,*diroption -thisbranch cmd "%(*setcust X_bg:T_%%%%n=20 %%%%: *setcust X_bg:P_%%%%n=%FCD %%%%: %%%%K"loadcust"%) %%: %%K"@Q" %: *opensubwin %1,壁紙にする画像ファイルを選択してください
サブ窓が開くので、壁紙にしたい画像ファイルにカーソルをあわせ、Shift+ENTERを押す。
```

F5を押して、背景画像が変更されていたら成功。

## 元に戻したい場合

変更した背景色や背景画像をもとに戻したい場合は、コマンドを実行したディレクトリで、以下のコマンドを実行すればいい。

```
*diroption -thisbranch cmd ""
```
