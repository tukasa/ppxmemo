---
title: ImageMagick
part: 外部ソフト
date: 2023-01-16
---
[ImageMagick](https://imagemagick.org/index.php)を使ってPPxで

- 左に90度回転
- 右に90度回転
- 拡大縮小
- 拡張子を変換
- 複数の画像ファイルをPDFに

ができるようにする。

以下を編集して取込。これで、拡張子がJPG、PNG、JPEG、BMPのファイル上でShift+Enterを押せば、画像処理メニューが出る。

```text
{% raw %}
-|M_Picture =
A_exec = { ; エイリアス
imagemagic = "C:\Program Files\ImageMagick-7.0.9-Q16\magick.exe"
}

M_Picture = { ** comment **
ペイント(&P) = mspaint %FCD
-- =
左に90度回転(&L) = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' mogrify -auto-orient -rotate 270 @%*name(C,"%so"response"")
右に90度回転(&R) = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' mogrify -auto-orient -rotate 90 @%*name(C,"%so"response"")
拡大縮小 = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' mogrify -geometry %"数値を入力してください"%{30%}%% @%*name(C,"%so"response"")
拡張子を変換 = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' mogrify -format %"拡張子を入力してください"%{%|%t%|%} @%*name(C,"%so"response"")
画像ファイルをPDFに = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' @%*name(C,"%so"response"") %"拡張子を入力してください"%{%FD\%|hoge%|.pdf%}
-- =
壁紙にする(&W) = *customize X_bg:Path=%FDC %: *customize X_bg:Type=10
}

E_scr = { ; \[Enter]用判別
JPG ,%M_Picture,A
PNG ,%M_Picture,A
JPEG ,%M_Picture,A
BMP ,%M_Picture,A
}
{% endraw %}
```