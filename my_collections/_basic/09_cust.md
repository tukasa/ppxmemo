---
title: ツールバー
tags: 基本的なカスタマイズ
date: 2022-03-31
last_modified_at: 
---

## ボタン用アイコンの準備

使用したいアイコン画像を、横並びに連結した画像ファイルを用意する。使用できる画像形式はbmpだが、各種プラグインがあれば他の形式でもいいみたいだ。

![alt]({{ "/assets/images/toolbar002.png" | relative_url }})

## カスタマイザーでメニューを作成

カスタマイザーを開き、ボタンタブを選択する。

「種類」に表示されているのは登録済みのメニュー。B_から始まるのがツールバーメニューで、HM_から始まるのが隠しメニューだ。
まずは、「PPc標準ツールバー /B_cdf」を選択してみよう。

![alt]({{ "/assets/images/toolbar003.png" | relative_url }})

青い線で囲った箇所に、メニュー名「B_cdef」が入力されている。これを消して、新規メニュー名を入力する。ここでは「B_test」とする。

![alt]({{ "/assets/images/toolbar004.png" | relative_url }})

参照をクリックし、先に準備した画像を選択する。これでアイコン一覧が表示される。

![alt]({{ "/assets/images/toolbar005.png" | relative_url }})

1. 利用したいアイコンをクリック
1. 項目名に、ツールチップに表示する文字列を記述
1. 登録内容詳細に、実行する内容を記述
1. 設定をクリック

![alt]({{ "/assets/images/toolbar006.png" | relative_url }})

すると、新たにツールバーメニューB_testが作成され、そこに先に登録した項目が登録される。

![alt]({{ "/assets/images/toolbar007.png" | relative_url }})

次いで、２つ目の項目を登録する。

1. 「種類」からB_testを選択
1. 右上から新規を選択
1. 利用したいアイコンをクリック
1. 項目名に、ツールチップに表示する文字列を記述
1. 登録内容詳細に、実行する内容を記述
1. 設定をクリック

![alt]({{ "/assets/images/toolbar008.png" | relative_url }})

これで、二つ目の項目が登録される。 同様にして、項目を追加していく。

項目を全て追加したら、適用をクリックしよう。

## 作成したツールバーを登録


「メニューバー - 表示 - レイアウト - 上部ドック」から、先に作成したツールバー（ここではB_test)を選択する。

![alt]({{ "/assets/images/toolbar010.png" | relative_url }})

 これで、B_testが登録される。

![alt]({{ "/assets/images/toolbar011.png" | relative_url }})

