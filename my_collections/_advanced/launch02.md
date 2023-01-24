---
title: 補完候補リストの切り替え
part: 一行編集の活用
created_at: 2023-01-25
---

一行編集に読み込ませる補完候補ファイルは、切り替えることができる。
コマンドを記載したcmd_list.txtと、ファイルパスを記載したpath_list.txtをPPxフォルダに作成しよう。

_cmd_list.txt_

```text
*ppb
*ppcust
*ppcust /edit ;編集して取込
*monitoroff
*reboot ;Windows を再起動
*shutdown ;Windows をシャットダウン
```

_path_list.txt_

```text
D:\bin\afxw\AFXW.EXE
D:\bin\afxw\AFXWCFG.EXE
D:\bin\AIMP4\AIMP.exe
D:\bin\DialogHandler\DialogHandler.x86-64.exe
D:\bin\dyna\Dyna.exe
D:\bin\EasyShot\EasyShot.exe
```

以下を編集して取込。

```text
_Command	= {	; ユーザコマンド・関数
changelist	= *completelist -set -file:"%*arg(1)" %: *completelist -close %: *replace ""
	*ifmatch 0,0%*arg(1) %: *setcaption no list %: *stop
	*setcaption %*arg(1)
}

K_lied	= {
'@'	,*RotateExecute liedlist, *changelist %%0cmd_list.txt, *changelist %%0path_list.txt,*changelist
}
```

一行編集上で[@]を押すことで、読み込ませる補完候補リストを切り替えることができる。
