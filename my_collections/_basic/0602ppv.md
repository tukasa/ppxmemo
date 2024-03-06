---
title: 連動ビュー
part: PPv
created_at: 2023-07-28
last_modified_at: 
---

大きくは以下の2つの場合がありうる。

- PPc中心
- PPv中心

## PPc中心

![PPc中心連動ビュー]({{ "/assets/images/aboutppv05.gif" | relative_url }})

PPc上で\\[Y]で連動ビューになる。PPcでカーソルを動かすと、それにあわせてPPvの表示ファイルも切り替わる。

## PPv中心

![PPv中心連動ビュー]({{ "/assets/images/aboutppv06.gif" | relative_url }})

%vやPPcの[N]、[Y]でPPvを呼び出した場合、PPv上で^[←] ^[→]で連動ビューができる。呼び出し元PPcのカーソルが移動した後、カーソル上のファイルがPPvで表示される。
*ppvで呼び出した場合は、呼び出し元PPcの情報がPPvに伝わらないため、この機能は使えない。"-setparent:%N"により、呼び出し元PPcを指定する必要がある。
