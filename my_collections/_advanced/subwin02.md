---
title: 7-ZIP
part: サブ窓
date: 2023-01-13
---

7-ZIPを使い、解凍や圧縮をする。
以下をScriptフォルダに保存。

_wrap_7z.js_
```text
//!*script
// 7-zipを利用して展開/圧縮/個別圧縮を行う
// 第一引数: オプション u:展開 p:圧縮 ip:個別圧縮
// 第二引数: レスポンスファイル
// 第三引数: 処理先フォルダ
//
// コマンド例
// 展開:*script %0\Script\wrap_7z.js,u,%a*8FCDN,%2
// 圧縮:*script %0\Script\wrap_7z.js,p,%a*8FCDN,%*input("%2%*addchar(\)|%*extract(C"%%X")|.zip" -title:"7zipで圧縮" -select:i)

// 個別圧縮:*script %0\Script\wrap_7z.js,ip,%a*8FCDN,%2

if (PPx.Arguments.Length < 3){
  PPx.SetPopLineMessage("引数が正しくありません。");
  PPx.Quit(-1);
}

//  7z.exeのパス
//var Exec = "C:\\Program Files\\7-Zip\\7z.exe";
var Exec = PPx.Extract('%\'7z\'');

var option = PPx.Arguments.Item(0);
var responseFile = PPx.Arguments.Item(1);
var outputFolder = PPx.Arguments.Item(2);

var fso = PPx.CreateObject("Scripting.FileSystemObject");
var archiveList = GetList(responseFile);
var parentFolder = fso.GetParentFolderName(archiveList[0]);

if (option == "u") {
  // 展開
  for (x in archiveList){
    if (archiveList[x] == ""){
      break;}
    PPx.Execute('%OBsq '+Exec+' x -o\"'+outputFolder+'\\*\" \"'+archiveList[x]+'\"');
  }
} else if (option == "p") {
  // 圧縮
  var sorceFiles = "";
  for (x in archiveList){
    if (archiveList[x] == ""){
      break;}
    sorceFiles += '\"' + fso.GetFileName(archiveList[x]) + "\" "
    }
  PPx.Execute('*cd '+parentFolder+' %: %OBsq '+Exec+' a \"'+outputFolder+'\" '+sorceFiles);
} else if (option == "ip") {
  // 個別圧縮
  // フォルダの時は入れ子構造を避けるパターン。
  for (x in archiveList){
    if (archiveList[x] == ""){
      break;}
    var fullpath=PPx.Extract('%*name(CDN,\"'+archiveList[x]+'\",\"%1\")');
    if(PPx.GetFileInformation(fullpath)==":DIR"){
      PPx.Execute('*cd \"'+fullpath+'\" %: '+Exec+' a \"'+outputFolder+'\\'+fso.GetBaseName(archiveList[x])+'.zip\" *');
    } else {
      PPx.Execute('%OBsq '+Exec+' a \"'+outputFolder+'\\'+fso.GetBaseName(archiveList[x])+'.zip\" \"'+archiveList[x]+'\"');
    }
  }
  // フォルダでも入れ子構造を避けないパターン
  /*
  for (x in archiveList){
    if (archiveList[x] == ""){
      break;}
    PPx.Execute(Exec+' a \"'+outputFolder+'\\'+fso.GetBaseName(archiveList[x])+'.zip\" \"'+archiveList[x]+'\"');
  }
   */
}

// レスポンスファイルからファイル名のリストを作成
function GetList(list)
{
  var f = CreateObject("ADODB.Stream");
  
  f.type = 2;
  f.charset = "UTF-8";
  f.open;
  f.LoadFromFile(list);
  text = f.readText(-1).split("\r\n");
  f.close;
  return text;
}
```

以下を編集して取込。

```text
KC_main    = {
\U ,*setcust _User:temp_exec=*script %0\Script\wrap_7z.js,u,%%*extract(%n"%%%%a*8FCDN"),%%%1 %%: %%K"@Q"
	*opensubwin %FCD,展開先のフォルダを選択してください
\P ,*setcust _User:temp_exec=*script %0\Script\wrap_7z.js,p,%%*extract(%n"%%%%a*8FCDN"),%%*input("%%1%%*addchar(\)|%%*extract(C"%%%%X")|.zip" -title:"7zipで圧縮" -select:i) %%: %%K"@Q"
	*opensubwin %FCD,圧縮先のフォルダを選択してください}
\I ,*setcust _User:temp_exec=*script %0\Script\wrap_7z.js,ip,%%*extract(%n"%%%%a*8FCDN"),%%%1 %%: %%K"@Q"
	*opensubwin %FCD,個別圧縮先のフォルダを選択してください}
}
```

- \U: サブ窓を使って7-Zipで展開
- \P: サブ窓を使って7-Zipで圧縮
- \I: サブ窓を使って7-Zipで個別圧縮

となる。

