---
title: 设置出生点
---

想在服务器中重新设置出生点？

## 使用命令`/setworldspawn`

找到服务器控制台

![曾小皮艾草](/img/pages/Terminal.png)

输入以下命令：

```text
setworldspawn X Y Z [<yaw> <pitch>]
```

注：

- 控制台输入此命令必须加上坐标；可附加 `[<yaw> <pitch>]` 指定出生朝向
- 出生点随机散布范围由 `respawn_radius` 规则控制（1.21.11+/26.x；旧版名为 `spawnRadius`/`spawnChunkRadius`）

或者你也可以在游戏内使用此命令（可直接复制，游戏内`ctrl+v`粘贴）。

```text
/setworldspawn
```