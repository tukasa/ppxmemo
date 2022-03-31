---
title: Key Module
tag: module
---
## nストロークキー入力とはなにか

PPXKEY.DLL（64bitならPPXKEY64.DLL）をPPxフォルダに入れると、nストロークキー入力に必要な`*setnextkey`を使えるようになる。
nストロークキー入力というのは、Emacsやxyzzyである操作方法。

メモ帳などの通常のエディタは、

- C-x 切り取り

というように、ひとつのキーにはひとつの操作しか割り振ることができない。

だが、xyzzyのように2ストロークキー入力ができるエディタだと、

- C-x s 複数バッファを上書き保存
- C-x C-c エディタを終了する
- C-x 0 カレントウィンドウを削除

というように、C-xを押したあとに続けて何を押すかによって複数の操作を割り振ることができる。

1ストロークキー入力だと、「アルファベットの数×修飾キーの組み合わせ」の中からさらに、ホームポジションからの押しやすさ、覚えやすさ等で絞られ、使えるキーボードショートカットはそれほど多くはない。それに比較して格段に、扱えるキーボードショートカットが増えるわけだ。

PPxでは、このnストロークキー入力をすることができる。

## 2ストロークキー入力

- C-x aでaaaaと表示
- C-x bでbbbbと表示

したければ次のようにする。ちなみに C-x a は「Ctrl＋Xを押したあと、Aキーを押す」の意味。

```text
KC_main = { ; PPcメイン窓
^X ,*setnextkey K_user1
}

K_user1 = {
a , echo aaaa
b , echo bbbb
}
```

## 3ストロークキー入力

- C-x aでaaaaと表示
- C-x bでbbbbと表示
- C-x c aでhomuと表示
- C-x c bでhomuhomuと表示

したい場合は次のようにする。

```text
KC_main = { ; PPcメイン窓
^X ,*setnextkey K_user1
}

K_user1 = {
a , echo aaaa
b , echo bbbb
c , *setnextkey K_user2 ; 3ストロークキー入力
}

K_user2 = {
a , echo homu
b , echo homuhomu
}
```

同じ要領でキーマップを増やしていけば、４ストロークキー入力、５ストロークキー入力も可能になる。
