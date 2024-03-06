---
title: コメントファイル
part: その他
created_at: 2023-07-12
last_modified_at: 
---

カレントディレクトリに00_INDEX.txtというファイルがあれば、その内容に応じてエントリにコメントを付けることがことができる。
まずは00_INDEX.TXTを作成し、各行が「エントリ名 コメント」となるように編集しよう。

_00_INDEX.TXT_
```text
20230510-145859-0.JPG	ガトーショコラ
20230525-144755-0.JPG	NYチーズケーキ
20230619-154351-0.JPG	ガトーショコラ
20230626-152551-0.JPG	レモンカード
```
![PPc通常表示]({{ "/assets/images/other10.png" | relative_url }})

次に[;]で表示形式メニューを出し、「サムネイル2」を選択する。これで、各エントリのコメントを表示することができる。

![PPcサムネイル2]({{ "/assets/images/other11.png" | relative_url }})

主な用途は以下の2つだ。

- エントリのメモの保存
- エントリから取得した特殊な情報の表示

## コメントの編集

直接00_INDEX.TXTを編集する以外に、*commentでもコメントを操作することができる。
カーソル位置エントリのコメントを編集したい場合は、以下のようになる。

```text
{% raw %}*comment "%ee%"コメントの編集"%{%*comment%|%}"{% endraw %}
```

コメントを編集したときの保存方法は、XC_cwrtで設定できる。

## コメントの一括編集

*commentで全エントリのコメントを操作することもできる。

```text
*comment all extract,"%%FT"
```

コマンドでは取得できない情報をコメントにする場合は、スクリプトを利用することになる。[howmファイルのタイトル表示]({{ "/advanced/0601moe" | relative_url }})にあるtitle2comment_all.jsは、howmファイルのタイトルをコメントにするスクリプトだ。参考にしてみてほしい。