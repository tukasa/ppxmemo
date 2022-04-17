---
title: ファイル判別の新規作成
tags: 基本的なカスタマイズ
date: 2022-03-31
last_modified_at: 2022-03-31
---

## 拡張子判別パターンの作成

カスタマイザーを開き、ファイル判別タブを選択する。種類のところに、既存のファイル判別パターンの名前（ここではE_cr）が入力されている。これを消して、新規に作りたいパターンの名前を入力する。ここでは、E_testとしよう。

![alt]({{ "/assets/images/hanbetunew01.png" | relative_url }})

ついで、判別名に拡張子を。登録内容詳細に、その拡張子で実行したい内容を書き、設定をクリック。

![alt]({{ "/assets/images/hanbetunew02.png" | relative_url }})

すると、新たな種類E_testが作成され、そこに先の拡張子判別が登録される。

![alt]({{ "/assets/images/hanbetunew03.png" | relative_url }})

次に、２つ目の拡張子を登録する。左上の種類から、先に作成したパターン（E_test）を選択。右上から新規を選択したあと、項目名と登録内容を埋めて、設定を押す。

![alt]({{ "/assets/images/hanbetunew04.png" | relative_url }})

同様にして、拡張子を登録していく。全て登録し終えたら、適用をクリックしよう。
こうして作成した拡張子別判別は、`%ME_xxx`で実行することができる。