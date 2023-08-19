---
title: zoxide
part: 外部ソフト
created_at: 2023-07-03
---
[zoxide](https://github.com/ajeetdsouza/zoxide)を使い、頻繁に使うディレクトリへ高速に移動できるようにする。

![zoxide]({{ "/assets/images/zoxide01.gif" | relative_url }})

## 準備

- [NYAGOS](https://github.com/nyaosorg/nyagos)
- [zoxide](https://github.com/ajeetdsouza/zoxide)
- [fzf](https://github.com/junegunn/fzf)

をインストールする。[Scoop](https://scoop.sh/)や[Chocolatey](https://chocolatey.org/)といったパッケージ管理ソフトを使うと、パスを勝手に通してくれて便利だ。

以下をPPxフォルダに保存。

_jumppath.lua_

```
hoge = nyagos.eval("zoxide query -i")
nyagos.exec(arg[1] .. "PPBW.EXE -c *execute C,*jumppath \"" .. hoge .. "\"")
```

以下を編集して取込。

```
KC_main = {
LOADEVENT ,*ifmatch "o:e,!a:a",%1 %: %Obcd zoxide add "%1"
}
Mes0411	= {
EXEF	= 
}
```

## やり方

以下を実行する。

```text
%Oq *run -noppb -pos:%*windowrect(,l),%*windowrect(,t) nyagos -f %0jumppath.lua %0
```
