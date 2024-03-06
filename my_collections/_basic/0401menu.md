---
title: メニューの作り方
part: メニュー
created_at: 2022-03-31
last_modified_at: 2023-07-22
---

## GUIによるカスタマイズ

メニュータブを選択する。

![メニュータブ]({{ "/assets/images/menu01.png" | relative_url }})

種類のところに、既存のメニュー名（ここではM_pjump）が入力されている。これを消して、新規に作りたいメニュー名を入力する。ここでは、M_testというメニュー名にしよう。
次いで、個々の項目を登録。項目名と登録内容を記入して、設定を押す。

![設定ボタン]({{ "/assets/images/menu03.png" | relative_url }})

すると、新たにM_testメニューが作成され、そこに先に登録した項目が登録される。

![登録内容の欄]({{ "/assets/images/menu04.png" | relative_url }})

次に、２つ目の項目を登録する。左上の種類から、先に作成したメニュー（M_test）を選択。右上から新規を選択したあと、項目名と登録内容を埋めて、設定を押す。

![2つ目の項目を登録]({{ "/assets/images/menu05.png" | relative_url }})

同様にして、項目を追加していく。

区切り線を挿入したい場合は、線挿入をクリックして、挿入したいものを選択。登録内容は空欄でいい。

![区切り線]({{ "/assets/images/menu06.png" | relative_url }})

項目を全て追加したら、適用をクリックしよう。

## テキスト編集によるカスタマイズ

「表示内容 = 項目内容」の形式で記載する。

```text
-|M_test=

M_test = {
Systemメニュー = %K"@&SPACE"
最小化 = %K"@\ESC"
-- =
Help表示 = %K"@F1"
}
```

## メニューの表示

作成したメニューは`%M_xxx`(ここでの例なら`%M_test`)で表示できる。

![メニュー表示]({{ "/assets/images/menu07.png" | relative_url }})
