---
title: 常用 gamerule 速查
---

::::tip

`gamerule`（游戏规则）是控制世界行为的开关。和 [server.properties](./20-serverproperties.md) 不同，gamerule **存储在存档里**，改完立即生效、不用重启服务器。

- 在控制台输入 `gamerule <名称> <值>`（不带斜杠）。
- 在游戏里输入 `/gamerule <名称> <值>`（需要[启用作弊与权限](1-JECommonQuestions/3-online_mode.md)，OP 默认权限等级 2 即可）。
- 查看当前值：`gamerule <名称>` 不带值。
- 列出全部 gamerule：`gamerule` 不带参数。

::::

::::warning 命名规则在 1.21.11 改了

**1.21.10 及以下**用驼峰命名（camelCase）：`keepInventory`、`mobGriefing`、`randomTickSpeed`。
**1.21.11+ / 26.x 起**全部改为蛇形命名（snake_case）：`keep_inventory`、`mob_griefing`、`random_tick_speed`。

在旧版本服务器上用新名字会报 `Unknown game rule`，反之亦然。本文同时给出两种写法。

::::

## 最常用

| gamerule | ≤1.21.10 | ≥1.21.11 | 默认 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| 死亡不掉落 | `keepInventory` | `keep_inventory` | `false` | `true` 时玩家死亡后保留物品栏与经验。[详见](1-JECommonQuestions/5-keepinventory.md) |
| 生物破坏 | `mobGriefing` | `mob_griefing` | `true` | `false` 时苦力怕/末影人/劫掠兽等不破坏方块，村民不种地，羊不吃草。[详见](1-JECommonQuestions/7-mobGriefing.md) |
| 随机刻速度 | `randomTickSpeed` | `random_tick_speed` | `3` | 控制作物生长、火势蔓延、冰块融化等随机事件发生频率；`0` 完全停止 |
| 立即重生 | `doImmediateRespawn` | `immediate_respawn` | `false` | `true` 跳过死亡界面直接重生 |
| 玩家睡眠百分比 | `playersSleepingPercentage` | `players_sleeping_percentage` | `100` | 跳过夜晚需要的入睡玩家百分比；`0` 则一名玩家睡即可 |
| 禁用袭击 | `disableRaids` | `raids` | `true`/`false` | ≤1.21.10 写法为 `disableRaids`（`true`=禁用）；≥1.21.11 改为 `raids`（`false`=禁用）——注意**语义反转** |
| 自然恢复 | `naturalRegeneration` | `natural_health_regeneration` | `true` | `false` 关闭饥饿回血（UHC 常用） |
| 免摔 | `fallDamage` | `fall_damage` | `true` | `false` 关闭摔落伤害 |
| 免溺 | `drowningDamage` | `drowning_damage` | `true` | `false` 关闭溺水伤害 |
| 免冻 | `freezeDamage` | `freeze_damage` | `true` | `false` 关闭冰冻伤害 |
| 火焰伤害 | `fireDamage` | `fire_damage` | `true` | `false` 关闭火焰伤害 |
| 时间前进 | `doDaylightCycle` | `advance_time` | `true` | `false` 锁定时间 |
| 天气循环 | `doWeatherCycle` | `advance_weather` | `true` | `false` 锁定天气 |
| 生物生成 | `doMobSpawning` | `spawn_mobs` | `true` | `false` 全维度禁刷怪 |
| 怪物生成 | `spawnMonsters` (≤1.21.9 也是 server.properties 键) | `spawn_monsters` | `true` | `false` 仅禁怪物，动物照常 |
| TNT 爆炸 | `tntExplodes` | `tnt_explodes` | `true` | `false` 时 TNT 不炸方块（与 `mobGriefing` 无关） |
| 命令方块工作 | `commandBlockOutput`/`enableCommandBlock` (≤1.21.9 是 server.properties) | `command_blocks_work` | `true` | `false` 禁用命令方块 |
| 发送命令反馈 | `sendCommandFeedback` | `send_command_feedback` | `true` | `false` 控制台/玩家不回显命令执行结果 |
| 管理员命令日志 | `logAdminCommands` | `log_admin_commands` | `true` | `false` 不把命令写进 `logs/` |
| 显示死亡信息 | `showDeathMessages` | `show_death_messages` | `true` | `false` 隐藏死亡广播 |
| 显示进度信息 | `announceAdvancements` | `show_advancement_messages` | `true` | `false` 隐藏进度达成广播 |
| 缩减调试信息 | `reducedDebugInfo` | `reduced_debug_info` | `false` | `true` 时 F3 调试信息只显示坐标，隐藏区块/朝向等 |
| 旁观生成区块 | `spectatorsGenerateChunks` | `spectators_generate_chunks` | `true` | `false` 旁观模式不加载新区块（省内存） |
| 出生半径 | `spawnRadius` (≤1.20.4) / `spawnChunkRadius` (1.20.5~1.21.10) | `respawn_radius` | `10` | 玩家重生的随机偏移半径；与 [setworldspawn](1-JECommonQuestions/4-setworldspawn.md) 配合 |
| 实体挤压上限 | `maxEntityCramming` | `max_entity_cramming` | `24` | 单格内实体数量超过此值会互相挤压致死 |
| 雪球累积高度 | `snowAccumulationHeight` | `max_snow_accumulation_height` | `1` | 雪的堆叠层数上限（0=不堆雪） |
| 矿车最高速度 | `minecartMaxSpeed` | `max_minecart_speed` | `8` | 矿车最高时速（实验性铁路改进在 1.21.2+） |
| 火焰蔓延半径 | `fireSpreadRadius` (1.21.6+) | `fire_spread_radius_around_player` | `128` | 火焰以玩家为中心的蔓延检测半径 |
| 通用仇恨 | `universalAnger` | `universal_anger` | `false` | `true` 时激怒的中立生物会攻击**所有**玩家而非只攻击挑衅者 |
| 宽恕死亡玩家 | `forgiveDeadPlayers` | `forgive_dead_players` | `true` | `false` 时激怒的中立生物即使玩家死亡也不会停止仇恨 |
| 水源转换 | `waterSourceConversion` | `water_source_conversion` | `true` | 两个水源相邻能否生成新水源（关闭可堵无限水） |
| 熔岩源转换 | `lavaSourceConversion` | `lava_source_conversion` | `false` | `true` 开启岩浆源再生（1.19.3+，默认关） |
| 藤蔓蔓延 | `spreadVines` | `spread_vines` | `true` | `false` 阻止藤蔓/发光浆果/洞穴藤蔓蔓延 |
| 生物战利品掉落 | `doMobLoot` | `mob_drops` | `true` | `false` 生物不掉物品（含经验球） |
| 方块掉落 | `doTileDrops` | `block_drops` | `true` | `false` 破坏方块不掉物品（含经验球） |
| 实体掉落 | `doEntityDrops` | `entity_drops` | `true` | `false` 实体（盔甲架、物品展示框等）不掉落 |
| 经验球消失 | `enderPearlsVanishOnDeath` | `ender_pearls_vanish_on_death` | `true` | `false` 时死亡前投掷的末影珍珠仍会传送 |
| 定位条 | `locatorBar` | `locator_bar` | `true` | `false` 隐藏屏幕下方玩家位置指示条（1.21.6+） |
| 全球音效事件 | `globalSoundEvents` | `global_sound_events` | `true` | `false` 关闭全服广播音效（如 Boss 战音乐/末影龙死亡音） |
| 限制合成 | `doLimitedCrafting` | `limited_crafting` | `false` | `true` 时玩家只能合成已解锁的配方 |
| 抛射物破坏方块 | `projectilesCanBreakBlocks` | `projectiles_can_break_blocks` | `true` | `false` 时箭/火球等抛射物不打碎细弱方块 |
| 刷怪笼工作 | `spawnerBlocksWork` | `spawner_blocks_work` | `true` | `false` 禁用刷怪笼 |
| 劫掠兽/幻翼/行商/监守者刷 | `doPatrolSpawning` / `doInsomnia` / `doTraderSpawning` / `doWardenSpawning` | `spawn_patrols` / `spawn_phantoms` / `spawn_wandering_traders` / `spawn_wardens` | 各 `true` | 分别控制袭击小队、幻翼、流浪商人、监守者的自然生成 |
| 下界传送门 | `allowEnteringNetherUsingPortals` (≤1.21.9 也是 server.properties) | `allow_entering_nether_using_portals` | `true` | `false` 禁止通过下界门进入下界 |
| 鞘翅移动检测 | `elytraMovementCheck` | `elytra_movement_check` | `true` | `false` 关闭鞘翅飞行检测（防误踢，与 `allow-flight` 互补） |
| 玩家移动检测 | `playerMovementCheck` | `player_movement_check` | `true` | `false` 关闭玩家移速检测 |
| PVP | `pvp` (≤1.21.9 也是 server.properties) | `pvp` | `true` | `false` 玩家间不可伤害 |
| 方块/生物爆炸掉率衰减 | `blockExplosionDropDecay` / `mobExplosionDropDecay` / `tntExplosionDropDecay` | `block_explosion_drop_decay` / `mob_explosion_drop_decay` / `tnt_explosion_drop_decay` | 各 `true` | `false` 爆炸摧毁的方块/生物完整掉落而非按距离衰减 |
| 最大指令分叉 | `maxCommandForks` | `max_command_forks` | `65536` | `execute as @e` 分叉上限 |
| 最大指令长度 | `maxCommandChainLength` | `max_command_sequence_length` | `65536` | 单函数/命令链最多指令数 |
| 最大方块修改数 | `commandModificationBlockLimit` | `max_block_modifications` | `32768` | 单次 `fill`/`clone` 修改方块上限 |
| 下界传送门延迟 | `playersNetherPortalDefaultDelay` / `playersNetherPortalCreativeDelay` | `players_nether_portal_default_delay` / `players_nether_portal_creative_delay` | `80`/`1` | 玩家站进下界门到传送的游戏刻数（生存/创造） |

## 已移除或迁移的"gamerule"

下列条目在 1.21.9 之前是 `server.properties` 键，**1.21.9 起**由 Mojang 移到了 gamerule：

| 旧 server.properties 键 | 新 gamerule |
| :--- | :--- |
| `allow-nether` | `allow_entering_nether_using_portals` |
| `enable-command-block` | `command_blocks_work` |
| `spawn-animals` | `spawn_mobs`（与动物/怪物合并） |
| `spawn-monsters` | `spawn_monsters` |
| `spawn-npcs` | `spawn_mobs`（同上） |
| `pvp` | `pvp` |

如果你在 1.21.9+ 的 `server.properties` 里还写着这些键，启动时会报警告且不生效——改成 gamerule 即可。

## 常用组合

### 创造建筑服

```
gamerule spawn_mobs false
gamerule advance_weather false
gamerule advance_time false
gamerule mob_griefing false
gamerule keep_inventory true
```

### 生电 / 技术生存

```
gamerule random_tick_speed 3    # 保持默认
gamerule mob_griefing true      # 村民种地/羊吃草必需
gamerule players_sleeping_percentage 25   # 一人睡即可
```

### UHC / 竞技

```
gamerule natural_health_regeneration false
gamerule immediate_respawn true
gamerule show_death_messages true
gamerule locator_bar false
```

::::info 想看完整列表？

- 服务端根目录 `world` 存档里的 `level.dat` 用 NBT 存所有 gamerule 值；编辑存档前记得先备份。
- [Minecraft Wiki 游戏规则页](https://zh.minecraft.wiki/w/%E6%B8%B8%E6%88%8F%E8%A7%84%E5%88%99) 有逐条说明与历史版本变更。

::::
