---
title: ファイル判別の新規作成
part: ファイル判別
created_at: 2022-03-31
last_modified_at: 2023-07-22
---

## GUIによるカスタマイズ

カスタマイザーを開き、ファイル判別タブを選択する。種類のところに、既存のファイル判別パターンの名前（ここではE_cr）が入力されている。これを消して、新規に作りたいパターンの名前を入力する。ここでは、E_testとしよう。

![種類の指定]({{ "/assets/images/hanbetunew01.png" | relative_url }})

ついで、判別名に拡張子を。登録内容詳細に、その拡張子で実行したい内容を書き、設定をクリック。

![拡張子とコマンドを登録]({{ "/assets/images/hanbetunew02.png" | relative_url }})

すると、新たな種類E_testが作成され、そこに先の拡張子判別が登録される。

![追加された]({{ "/assets/images/hanbetunew03.png" | relative_url }})

次に、２つ目の拡張子を登録する。左上の種類から、先に作成したパターン（E_test）を選択。右上から新規を選択したあと、項目名と登録内容を埋めて、設定を押す。

![2つ目の拡張子登録]({{ "/assets/images/hanbetunew04.png" | relative_url }})

同様にして、拡張子を登録していく。全て登録し終えたら、適用をクリックしよう。

## テキスト編集によるカスタマイズ

- 判別方法,コマンドライン

という書式で記載する。

```text
E_test    = {
*	,editor %FCD
.	,editor %FCD
:DIR	= C_DIR
:JPEG	,
TXT	,editor %FCD
JPG	,mspaint %FCD
JPEG	,mspaint %FCD
PNG	,mspaint %FCD
}
```

- 「*」は該当設定がない場合に使われる
- 「.」は拡張子がないファイルに使われる
- 「:DIR」はディレクトリに使われる
- 「:JPEG」はファイルの中身からJPEGと判別したときに使われる
- 特定の名前、ワイルドカード、正規表現による判別も可能

## 拡張子判別の実行

作成したファイル判別は、`%ME_xxx`(ここでの例なら`%ME_test`)で実行することができる。
