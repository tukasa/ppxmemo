---
title: Key Moduleでキーバインドを一時的に変更
part: module
created_at: 2024-01-26
---
Paper Plane xUI Key Moduleをインストールすることで、キーバインドの一時的な変更ができるようになる。
まずは、使用したいキーバインド設定を用意し、それを取り込む。

```
K_mapkeytest = {
A	,*linemessage hogehoge
B	,*linemessage fugafuga
}
```

次に、以下のコマンドを実行する。

```
*mapkey use,K_mapkeytest
```

キーバインドを元に戻したい場合は、窓を閉じるか、以下のコマンドを実行する。

```
*mapkey delete,K_mapkeytest
```
