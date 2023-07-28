---
title: PPv
part: その他
created_at: 2023-07-28
last_modified_at: 
---

PPvは、テキスト/画像/16進ダンプと表示形式を切り換えて見ることができるマルチフォーマットビューア。
カスタマイズにおいて、大きく以下の2つのテーマがある。

- 表示形態
- 連動ビューの方法

## 表示形態

以下のように分けることができる。

- 単独で表示
- PPcに重ねて表示
- PPcに被せて表示
- PPcに組み込んで表示

### 単独で表示

![PPv単独表示]({{ "/assets/images/aboutppv01.png" | relative_url }})

他の窓とは無関係にPPvを起動する。デフォルトではこの形態になってるはずなので、これでよければ何もする必要はない。

### PPcに重ねて表示

![PPcに重ねて表示]({{ "/assets/images/aboutppv02.png" | relative_url }})

PPvをPPcに重ねて表示する。
%vやPPcの[N]、[Y]でPPvを呼び出すのであれば、X_vposで設定するといい。

```text
X_vpos	= 0	; PPcからの呼出時の表示位置 0:独立 1:PPc 2:反対窓 3:一体化窓
```

*ppvを用いる場合は、`-setparent:%N`を指定しないと、この設定が機能しないので注意。
他には、window moduleの`*fitwindow`でも同じことができる。

_現在窓PPcに重ねて表示_
```text
*ppv %FCD -k *fitwindow %NC,%%N,0
```

_反対窓PPcに重ねて表示_
```text
*ppv %FCD -k *fitwindow %~N,%%N,0
```

_一体化PPcに重ねて表示_
```text
*ppv %FCD -k *fitwindow %NC#,%%N,0
```

### PPcに被せて表示

![PPcに被せて表示]({{ "/assets/images/aboutppv03.png" | relative_url }})

PPcに被せて表示する。「PPcに重ねて表示」とは違い、タイトルバーは表示されない。

_現在窓PPcに被せて表示_
```text
*ppv -popup:%NC %FDC
```

_反対窓PPcに被せて表示_
```text
*ppv -popup:%~N %FDC
```

_一体化PPcに被せて表示_
```text
*ppv -popup:%NC# %FDC
```

### PPcに組み込んで表示

![PPcに組み込んで表示]({{ "/assets/images/aboutppv04.png" | relative_url }})

PPcに組み込んで表示する。PPcの窓位置を移動した場合、PPvもそれに追随する。ただし、チラつきが生じるという欠点がある。

_現在窓PPcに埋め込んで表示_
```text
*ppv -parent:%NC %FDC
```

_反対窓PPcに埋め込んで表示_
```text
*ppv -parent:%~N %FDC
```

## 連動ビューの方法

大きくは以下の2つの場合がありうる。

- PPc中心
- PPv中心

### PPc中心

![PPc中心連動ビュー]({{ "/assets/images/aboutppv05.gif" | relative_url }})

PPc上で\\[Y]で連動ビューになる。PPcでカーソルを動かすと、それにあわせてPPvの表示ファイルも切り替わる。

### PPv中心

![PPv中心連動ビュー]({{ "/assets/images/aboutppv06.gif" | relative_url }})

%vやPPcの[N]、[Y]でPPvを呼び出した場合、PPv上で^[←] ^[→]で連動ビューができる。呼び出し元PPcのカーソルが移動した後、カーソル上のファイルがPPvで表示される。
*ppvで呼び出した場合は、呼び出し元PPcの情報がPPvに伝わらないため、この機能は使えない。"-setparent:%N"により、呼び出し元PPcを指定する必要がある。
