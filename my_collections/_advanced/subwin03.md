---
title: アプリケーション関連付け
part: サブ窓
date: 2023-01-13
---

ファイルのアプリケーション関連付けをサブ窓で選択できるようにする。

```text
KC_main    = {
\ENTER    ,*ifmatch "o:e,a:d" %: %K"@\ENTER" %: *stop
    *ifmatch !0,0%*getcust(E_execList:%T) %: %ME_execList %FCD %: *stop
    *setcust _User:sorce_id=%n %: *setcust _User:sorce_wh=%NC
    *ppc -r -bootid:x -single -k %(*fitwindow %su"sorce_wh",%NC,20 %: *mapkey use,K_subwin %: *linemessage EXEファイルを選択してください %: *string i,temp_exec=%%Ob %%FCD %%*extract(%su"sorce_id""%%%%#FCD") %%: %%K"@Q" %%: *setcust E_execList:%%*extract(%su"sorce_id""%%%%FT"),%%FCD%)
\X    ,*setcust _User:sorce_id=%n %: *setcust _User:sorce_wh=%NC
    *ppc -r -bootid:x -single -k *jumppath %ME_execList -entry %(%: *fitwindow %su"sorce_wh",%NC,20 %: *mapkey use,K_subwin %: *linemessage EXEファイルを選択してください %: *string i,temp_exec=%%Ob %%FCD %%*extract(%su"sorce_id""%%%%#FCD") %%: %%K"@Q" %%: *setcust E_execList:%%*extract(%su"sorce_id""%%%%FT"),%%FCD%)
}
```

shift+Enterを押した時、カーソル下ファイルの拡張子がアプリケーションに関連付けられてるか否かによって以下のように分岐。

- 関連付け登録済み→登録したアプリケーションで実行する
- 関連付け未登録→別窓が開く。開きたいアプリケーションを選択してShift+Enterでカーソル下ファイルを実行し、かつ関連付け登録

Shift+Xを押した時は、登録、未登録に関わらず別窓が開く。

