---
title: 一行編集ウィンドウ
part: その他
created_at: 2023-07-10
last_modified_at: 2024-03-05
---

PPxでは、一行編集ウィンドウを表示し、そこに打ち込んだテキストを利用することができる。例えば

```text
*makefile %"ファイルの新規作成"%E
```

とすれば、任意の名前でファイルを作成することができる。

![一行編集ウィンドウ]({{ "/assets/images/other01.png" | relative_url }})

この一行編集ウィンドウについて、基礎的なことを解説する。

---

## 空欄の一行編集ウィンドウを表示

空欄の一行編集ウィンドウを表示したいときは、`%E`を使う。

```text
%E
```

![空欄]({{ "/assets/images/other02.png" | relative_url }})

---

## あらかじめテキストを挿入

一行編集ウィンドウにあらかじめテキストを挿入しておきたいときは、`%{...%}`を使う。

```text
%{tukasa.txt%}
```

![範囲編集]({{ "/assets/images/other03.png" | relative_url }})

カーソル位置は、`%|`で指定できる。カーソルを置きたい位置に`%|`を挟もう。


```text
%{tukasa.%|txt%}
```

![カーソル位置指定]({{ "/assets/images/other04.png" | relative_url }})

`%|`を二つ置くことにより、その間を選択した状態になる。

```text
{% raw %}%{tuka%|sa.%|txt%}{% endraw %}
```

![選択位置指定]({{ "/assets/images/other05.png" | relative_url }})

---

## 展開したマクロ文字を挿入

`%!macro`で、マクロ文字を展開したものを、一行編集ウィンドウにあらかじめ挿入することができる。

```text
{% raw %}%!C{% endraw %}
```

![展開したマクロ文字を挿入]({{ "/assets/images/other06.png" | relative_url }})

---

## キャッシュ付き部分編集

`%$macro`により、編集内容を使い回すことができる。例えば

1. ファイルを新規作成
2. エディタで編集

という場合は以下のようになる。

```text
{% raw %}*makefile %${%|.txt%} %: %Ob editor %${%|.txt%}{% endraw %}
```

---

## ウィンドウタイトルの編集

`%"..."` を範囲編集の前に置くことで、一行編集ウィンドウのタイトルを変更することができる。

```text
{% raw %}%"うにゃああああああああああああああああん(ﾉ*ФωФ)ﾉ"%{%}{% endraw %}
```

![windowtitle]({{ "/assets/images/other07.png" | relative_url }})

---

## %*input

![一行編集]({{ "/assets/images/launch01.png" | relative_url }})

一行編集でさらに高度なことを行いたいときには、`%*input`を使う。`%*input`を使うと、

- タイトル
- 編集するテキスト
- カーソル位置
- ダイアログ種類、ヒストリ種類、参照の動作

を指定することができる。以下はヘルプに載っている例。

```text{% raw %}
*linemessage {%*input("text" -title:"Input title" -mode:g)}
{% endraw %}```

さらに、`-k:"command line" `または`-k command line `により、一行編集開始時に任意のコマンドを実行することができる。特に`*completelist`が有用だ。

### 補完候補ファイル

`*completelist`の`-file`オプションを使うと、任意の補完候補ファイルを指定することができる。

```text
*linemessage %*input("" -mode:h -k:"*completelist -file:%%0launch.txt")
```

### 一覧内容の詳細な指定

`*completelist`の`-detail`オプションを使うと、補完一覧の内容を、その並び順も含めて指定することができる。

```text
*linemessage %*input("" -mode:h -k:"*completelist -detail:""hist alias"" ")
```
