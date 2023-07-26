---
title: Script Module
part: module
created_at: 2022-03-31
last_modified_at: 2023-06-01
---

PPXSCR.DLL（64bit版の場合はPPXSCR64.DLL）をPPxフォルダに入れると、スクリプトを使えるようになる。

## スクリプトの実行

_hoge.js_
```text
//!*script
PPx.Echo("Hello World");
```

`*script %0\Script\hoge.js`で実行できる。

## 指定した内容を展開

_fuga.js_
```text
//!*script
PPx.Result = PPx.Extract("%1");
```

`echo %*script(%0\Script\fuga.js)`で、PPx.Result に指定した内容を展開できる。

## 引数

_arg.js_
```text
//!*script

// 引数がなければ終了
if (PPx.Arguments.Length < 2){
  PPx.SetPopLineMessage("引数が正しくありません。");
  PPx.Quit();
}

PPx.Echo("第一引数は"+PPx.Arguments.Item(0)+"です。\n第二引数は"+PPx.Arguments.Item(1)+"です。");
```

`*script %0\Script\arg.js,hoge,fuga`で、hogeとfugaを引数に取り、スクリプトを実行する。

_arg2.js_
```text
//!*script

// 引数がなければ終了
if (PPx.Arguments.Length < 1){
  PPx.SetPopLineMessage("引数が正しくありません。");
  PPx.Quit();
}

PPx.Result  = PPx.Arguments.Item(0);
```

`echo %*script(%0\Script\arg2.js,hoge)`で、hogeを引数に取り、スクリプトを実行。指定した内容が展開される。

## インラインスクリプト実行

- *js,*js9,*jsc,*vbs
- %*js,%*js9,%*jsc,%*vbs

を使用すると、第一引数をスクリプトとして実行する。
Script Moduleでしかできない簡単な処理をさせたり、Script Moduleでしか取得できない情報を取得したりするのに利用する。

_カーソルを最初のエントリに移動_
```text
*js "PPx.EntryIndex = 2"
```

_エントリーマーク数を取得_
```text
*linemessage %*js("PPx.result=PPx.EntryMarkCount")
```

