---
title: PDFCPU
part: 外部ソフト
created_at: 2023-01-16
---
[pdfcpu](https://github.com/pdfcpu/pdfcpu)でよく使うコマンドをメニューにしてまとめてみた。
```text
-|M_pdfcpu =

A_exec = { ; エイリアス
pdfcpu = D:\bin\pdfcpu\pdfcpu.exe
}

M_pdfcpu	= {
抽出(&L)	=	pdfcpu trim -pages %*input("1|-2" -title:"抽出開始ページと終了ページ" -select:i -mode:n) %*name(CBD,"%R","%1") %*input("out|.pdf" -title:"アウトプットファイル名" -select:i -mode:c)
分割(&S)	 =	*makedir %Y %: pdfcpu split %*name(CBD,"%R","%1") %Y
ページ数を指定して分割	=	*makedir %Y %: pdfcpu extract -mode page -pages %*input("1|-2" -title:"開始ページと終了ページ" -select:i -mode:n) %*name(CBD,"%R","%1") %Y
削除(&D)	=	pdfcpu trim -pages %*input("1-,!2" -title:"削除したいページを !#-# !# で指定" -select:l -mode:n) %*name(CBD,"%R","%1") %*input("out|.pdf" -title:"アウトプットファイル名" -select:i -mode:c)
--	= 
マークした画像ファイルをPDFに	=	pdfcpu import %*input("out|.pdf" -title:"アウトプットファイル名" -select:i -mode:c) %#FC
マークしたPDFファイルを結合	=	pdfcpu merge %*input("out|.pdf" -title:"アウトプットファイル名" -select:i -mode:c) %#FC
--	= 
PDFファイルを複製	=	pdfcpu merge %*input("out|.pdf" -title:"アウトプットファイル名" -select:i -mode:c) %*name(CBD,"%R","%1") %*name(CBD,"%R","%1")
}
```
