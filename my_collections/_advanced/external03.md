---
title: xdoc2txt
part: 外部ソフト
created_at: 2023-01-16
---
[xdoc2txt](http://ebstudio.info/home/xdoc2txt.html)を使い、PDFやDOCの内容をプレビュー表示する。

![preview]({{ "/assets/images/preview.png" | relative_url }})

```text
E_TipView = {
pdf , %Obd doc2txt "%si"TipTarget"" | %0ppvw.exe -P%si"TipWnd"
doc , %Obd doc2txt "%si"TipTarget"" | %0ppvw.exe -P%si"TipWnd"
docx , %Obd doc2txt "%si"TipTarget"" | %0ppvw.exe -P%si"TipWnd"
jtd , %Obd doc2txt "%si"TipTarget"" | %0ppvw.exe -P%si"TipWnd"
}
```

エントリの右端のあたりをカーソルオーバーすると色が変わる。そこで左クリックするとプレビューが表示される。