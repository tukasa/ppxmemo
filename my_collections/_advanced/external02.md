---
title: ImageMagick
part: 外部ソフト
created_at: 2023-01-16
---
[ImageMagick](https://imagemagick.org/index.php)を使ってPPxで以下ができるようにする。

- 左に90度回転
- 右に90度回転
- 拡大縮小
- 拡張子を変換
- 画像ファイルをPDFに

```text
{% raw %}
-|M_ImageMagick =

A_exec = { ; エイリアス
imagemagic = "C:\Program Files\ImageMagick-7.0.9-Q16\magick.exe"
}

M_ImageMagick = {
左に90度回転(&L) = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' mogrify -auto-orient -rotate 270 @%*name(C,"%so"response"")
右に90度回転(&R) = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' mogrify -auto-orient -rotate 90 @%*name(C,"%so"response"")
拡大縮小 = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' mogrify -geometry %"数値を入力してください"%{30%}%% @%*name(C,"%so"response"")
拡張子を変換 = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' mogrify -format %"拡張子を入力してください"%{%|%t%|%} @%*name(C,"%so"response"")
画像ファイルをPDFに = %OB *cd %*name(DB,"%a*8FCDB") %: %'imagemagic' @%*name(C,"%so"response"") %"拡張子を入力してください"%{%FD\%|hoge%|.pdf%}
}

{% endraw %}
```