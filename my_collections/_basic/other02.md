---
title: ListFile
part: その他
created_at: 2023-01-23
last_modified_at: 2023-07-10
---

## ListFileについて

仮想ディレクトリを扱うためにあるのが、ListFileだ。
ListFileを作成する方法はいくつかあるが、簡単なのが*whereisだ。PPcで以下のコマンドを実行すると、カレントディレクトリ以下のファイル、ディレクトリが列挙されたresult.txtが作成される。

```text
*whereis -dir:on -search -listfile:result.txt
```

作成したresult.txtにカーソルをあわせ[ENTER]で、仮想ディレクトリに入ることができる。

![ListFileその1]({{ "/assets/images/other08.png" | relative_url }})

## 活用方法

ListFileは、

- あちこちのディレクトリに散らばっているよく使うファイルを１つのディレクトリにまとめたいとき。
- 外部の検索アプリケーションなどで得た結果一覧をPPcで参照・利用したいとき。

に活用できる。例えば以下のようなListFileを、手動なり外部アプリケーションなりで作成すればいいわけだ。

```text
;ListFile
D:\bin
D:\Data
D:\work
C:\Program Files\7-Zip
C:\Program Files\Git
D:\work\遊びタイガー.jpg
D:\work\幻想じゃねえよな.PNG
```

![ListFileその2]({{ "/assets/images/other09.png" | relative_url }})

## マーク・ハイライト状態の保存

ListFIleは、マーク・ハイライト状態を保存し、再現するのにも利用することができる。以下はHELPに載っている例。

- マークの記憶

```text
*string p,markinf=%*temp()markinf.txt %: *makelistfile "%sp"markinf"" -name -marked
```

- マークの再現

```text
*markentry -list:"%sp"markinf"" -mark
```

## ListFileへの追加と削除

ListFileへのファイルの追加・削除は、直接ListFileを編集する以外に、仮想ディレクトリに対する操作でも行うことができる。
追加したい場合は、追加したいファイルを仮想ディレクトリにコピーすればいい。コマンドの場合は`*ppcfile !copy,D:\Temp\hoge.txt\`のようになる。
削除したい場合は、[Ctrl+Shift+D]だ。
