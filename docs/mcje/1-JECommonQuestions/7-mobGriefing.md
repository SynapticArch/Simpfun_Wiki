---
title: 开启防爆
---

想在服务器中开启防爆？（关闭生物破坏）

## 使用命令

打开服务器控制台>终端

![《太简单了 我不做单纯是因为电脑无线网速慢死》By Twelve](/img/pages/Terminal.png)

输入以下命令(可直接复制，游戏内使用`ctrl+v`粘贴，控制台输入请去掉斜杠)：

```
/gamerule mobGriefing false
```

注：1.21.11+/26.x 起该规则改名为 `mob_griefing`，上述旧写法适用于 1.21.10 及以下版本。

:::caution

TNT依然可以造成破坏：
`mobGriefing` 本就不管 TNT——TNT 是否炸方块由 `tnt_explodes` 控制（战利品掉落另有 `tnt_explosion_drop_decay`）。

关闭 `mobGriefing` 的副作用：村民不种地不捡食（影响繁殖与刷铁机）、羊不吃草、雪傀儡不留雪、末影人不搬方块、劫掠兽与僵尸不破坏门和海龟蛋。

生电玩家不推荐把它设为 false，不然一些机器无法正常工作
:::
