---
title: 开启死亡不掉落
---

想在服务器中开启死亡不掉落（保留物品栏）？

## 使用命令

打开服务器控制台>终端

![《太简单了 我不做单纯是因为电脑无线网速慢死》By Twelve](/img/pages/Terminal.png)

输入以下命令(可直接复制，游戏内使用`ctrl+v`粘贴，控制台输入请去掉斜杠)：

```text
/gamerule keepinventory true
```

注：在BDS服务端执行`/gamerule`需要`allow-cheats=true`且玩家拥有op权限，详见[为服务器开启作弊](./2-allow_cheat.md)。

