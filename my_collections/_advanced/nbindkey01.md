---
title: nストロークキーの基本
part: nストロークキー
date: 2023-01-13
---
Paper Plane xUI Key Moduleをインストールすることで、nストロークキー入力ができるようになる。

## 2ストロークキー入力

- [C-x a]でaaaaと表示
- [C-x b]でbbbbと表示

したければ次のようにする。ちなみに[C-x a]は「Ctrl＋Xを押したあと、Aキーを押す」の意味。

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

- [C-x a]でaaaaと表示
- [C-x b]でbbbbと表示
- [C-x c a]でhomuと表示
- [C-x c b]でhomuhomuと表示

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
