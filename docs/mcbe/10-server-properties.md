---
title: 基岩版服务器配置文件介绍
---
## 翻译过后的配置文件
:::info

以下内容基于 BDS 1.20.14.01 的默认文件整理翻译 (使用 Google 和 DeepL 提供的翻译服务), 已对照 Minecraft Wiki 上 BDS 1.26.x 官方默认文件核对修正: 键值与 1.26.x 一致, 新版新增的键以"1.26.x 新增"标注, 另有部分未翻译的新键与脚本调试键见文末说明。

:::

```ini
server-name=Dedicated Server
# 服务器介绍（将显示在 服务器名称 下方）
# 允许任何字符，除了分号，也就是“;”。

gamemode=survival
# 为新玩家设置的游戏模式
# 允许值（请填写引号内的内容）: "survival",(生存) "creative"(创造), 和 "adventure"(冒险)

force-gamemode=false
# 简单来说就是强制使用服务器设置的游戏模式，具体请看下面来自 DeepL 的翻译：
# force-gamemode=false（或 server.properties 中未定义 force-gamemode）
# 防止服务器向客户端发送游戏模式值，而不是
# 游戏模式值之外的其他游戏模式值。
# 即使这些值是在创建世界后在 server.properties 中设置的。
# force-gamemode=true 会强制服务器发送游戏模式值到客户端。
# 除了服务器在创建世界时保存的游戏模式值之外
# 如果这些值是在创建世界后在 server.properties 中设置的。

difficulty=easy
# 设置世界难度
# 允许值(请填写引号内的内容): "peaceful"(和平), "easy"(简单), "normal"(普通), 或 "hard"(困难)

allow-cheats=false
# 为世界启用作弊模式，允许使用例如 /give 等指令。
# 允许值(请填写引号内的内容): "true"开 或 "false"关
# 这两个值再往下不会继续翻译，请知悉

max-players=10
# 最大玩家在线数量
# 允许值: 任何正整数

online-mode=true
# 所有连接的玩家都必须通过 Xbox Live 身份验证
# 如果关闭，则只有局域网玩家才不需要验证，远程游玩仍需通过 Xbox Live 身份验证
# 所以不如保持默认

allow-list=true
# 白名单
# 如果为 true, 只有 allowlist.json 中列出的玩家才能加入服务器
# (旧版本 BDS 中该键为 white-list=false, 白名单文件为 whitelist.json)
# 允许值(请填写引号内的内容): "true" or "false"

server-port=19132
# 服务器侦听的 IPv4 端口
# 允许值: 1~65535 范围内的整数
# 不用动，反正你动了面板也会改回来（

server-portv6=19133
# 服务器侦听的 IPv6 端口
# 当 transport=nethernet 时此项被忽略, 改为在 server-port 上开启双栈套接字
# 允许值: 1~65535 范围内的整数
# 简幻欢 暂不提供 IPv6 服务, 即使配置也不生效

# 1.26.x 新增: server-ip 留空绑定所有网卡, transport=raknet 时被忽略; server-udp-ports 配置 UDP 客户端传输端口, 支持多条目与端口映射, transport=raknet 时被忽略

transport=nethernet
# 服务器使用的传输协议 (1.26.x 新增)
# 允许值(请填写引号内的内容): "raknet", "nethernet"

enable-lan-visibility=true
# 允许在局域网内被发现
# 没啥用，可以改成 false
# 允许值(请填写引号内的内容): "true" or "false"

view-distance=32
# 最大视距，降低以提升服务器性能
# 允许值(以区块为单位): 大于或等于 5 的正整数

tick-distance=4
# 当玩家距离某个区块超过设定值后，该区块将会停止加载。
# 例子：你离耕地过远，农作物就会停止生长。
# 请考虑你的刷怪塔、红石机器等等，推荐保持默认。
# 允许值: 4~12 的整数

player-idle-timeout=30
# 玩家挂机时间超过设定分钟后将被踢出，如果为 0 就不会生效。
# 允许值: 任何非负整数

# 1.26.x 新增: allow-player-joining (默认 true) 设为 false 时玩家无法加入服务器, 除非脚本 (AsyncPlayerJoinBeforeEvent) 显式允许

max-threads=8
# 多线程，如果设置为 0 或不填，服务端将会使用尽可能多的线程。
# 允许值: 任何正整数

level-name=Bedrock level
# 地图文件夹和地图名字
# 可以填写任何字符，除了分号和文件名非法符号: "/\n\r\t\f`?*\\<>|\"

level-seed=
# 没有地图时生成世界使用的种子
# 留空应该会随机生成
# 允许值: 任何字符

default-player-permission-level=member
# 为新玩家设置的权限级别
# 允许值(请填写引号内的内容): "visitor"(访客), "member"(成员), "operator"(管理员)

texturepack-required=false
# 强制使用服务器上的资源包
# 对于反矿透资源包会有用，但也会导致玩家不能自定义资源包。
# 允许值(请填写引号内的内容): "true" or "false"

content-log-file-enabled=false
# 记录错误日志到文件
# 允许值(请填写引号内的内容): "true" or "false"

content-log-console-output-enabled=false
# 将内容错误日志输出到控制台 stdout (1.26.x 新增)
# 允许值(请填写引号内的内容): "true" or "false"

content-log-level=info
# 设置内容日志的最低级别, error 为最高级别 (1.26.x 新增)
# 允许值(请填写引号内的内容): "error", "warning", "info", "verbose"

# ==================
# 以下设置建议保持默认
# 接下来仅提供修正翻译
# 部分设置会提供些建议
# ==================

compression-threshold=1
# 确定要压缩的原始网络有效负载的最小大小
# 允许值(请填写引号内的内容): 0-65535

compression-algorithm=zlib
# 确定用于网络的压缩算法
# 允许值(请填写引号内的内容): "zlib", "snappy"

server-authoritative-movement-strict=false
# 对玩家位置更严格, 客户端会收到更多位置修正, 高延迟下可能影响玩家在移动方块附近的移动 (1.26.x 新键)
# 允许值(请填写引号内的内容): "true" or "false"

server-authoritative-dismount-strict=false
# 对玩家取消骑乘位置更严格, 高延迟时客户端会收到取消骑乘位置的修正 (1.26.x 新键)
# 允许值(请填写引号内的内容): "true" or "false"

server-authoritative-entity-interactions-strict=false
# 对实体交互更严格, 高延迟下会影响玩家之间的交互判定 (1.26.x 新键, 取代旧版 correct-player-movement 体系)
# 允许值(请填写引号内的内容): "true" or "false"

player-position-acceptance-threshold=0.5
# 客户端与服务器玩家位置差异的容忍度, 防止对未作弊玩家过于频繁地发送修正 (1.26.x 新键)
# 例如击退或被活塞推动时, 双方对移动开始时间的感知可能不同
# 数值越高服务器越宽容, 超过 1.0 会增加允许作弊的可能性

player-movement-action-direction-threshold=0.85
# 玩家的攻击方向和视线方向的差异量。
# 允许值(请填写引号内的内容): 0~1 内任何值
# 其中 1 表示玩家的视线方向和玩家的攻击方向必须完全一致。
# 0 表示两个方向可以相差 90 度（含 90 度）。
# 这个设置应该是用来限制第三人称视角的攻击范围

server-authoritative-block-breaking-pick-range-scalar=1.5
# 服务器与客户端同步计算方块挖掘操作, 以验证客户端能否在它认为可以时破坏方块 (1.26.x 新键, 取代旧版布尔开关 server-authoritative-block-breaking)
# 这个设置可能可以防秒挖掘(除了急迫效果)，请根据服务器配置选择。

# 以下旧键在 1.26.x 官方默认文件中已被移除或改名, 仅供运行旧版 BDS 时参考:
#   server-authoritative-movement=server-auth -> server-authoritative-movement-strict / player-position-acceptance-threshold
#   player-movement-score-threshold / player-movement-distance-threshold / player-movement-duration-threshold-in-ms -> 由上述新键取代
#   correct-player-movement -> server-authoritative-entity-interactions-strict
#   server-authoritative-block-breaking -> server-authoritative-block-breaking-pick-range-scalar

chat-restriction=None
# 允许值(请填写引号内的内容): "None", "Dropped", "Disabled"
# 这表示对每个加入服务器的玩家的聊天限制级别。
# 默认为 "None"，表示正常的自由聊天。
# "Dropped" 表示聊天信息被丢弃，不会发送到任何客户端。玩家会收到一条信息，告诉他们“聊天被禁用”。
# "Disabled" 表示除非玩家是操作员，否则聊天界面甚至不会出现。不会向玩家显示任何信息。

disable-player-interaction=false
# 如果为 "true"，服务器将通知客户端在与世界交互时应忽略其他玩家。这不是服务器权威。

client-side-chunk-generation-enabled=true
# 如果为 "true"，服务器将通知客户端，他们可以在玩家交互距离之外生成可视化区块。

block-network-ids-are-hashes=true
# 如果为 "true"，服务器将发送散列的区块网络 ID，而不是从 0 开始向上的 ID。 这些 ID 是稳定的，不会因其他区块的变化而改变。

disable-persona=false
# 仅限内部使用 (官方注释原文: Internal Use Only)
# 应该是禁用玩家的皮肤编辑器。

disable-custom-skins=false
# 如果为 "true"，则禁用玩家在 Minecraft 商店资产或游戏资产之外自定义的皮肤。 这用于禁用玩家自定义的可能具有攻击性的皮肤。

server-build-radius-ratio=Disabled
# 允许值(请填写引号内的内容): "Disabled" 或范围 0.0~1.0 中的任何值
# 如果为 "Disabled"，服务器将动态计算生成多少玩家视图，并将其余视图分配给客户端构建。
# 否则，服务器将根据重载比例来计算要生成多少玩家视图，而不考虑客户端的硬件能力。
# 仅在启用 client-side-chunk-generation-enabled 功能时有效
```

## 隐藏的 op-permission-level
在 BDS 压缩包内置的文档及 Minecraft Wiki 中，有一个未出现的配置，这个配置在 Java 版是默认写在配置文件里的，但在基岩版的配置文件并未出现。

但它却有作用，当设置为 4 之后，最明显的区别就是：游戏设置内的世界选项变得可以调整，例如打开坐标显示、死亡不掉落等设置。

如何使用？在 **server.properties** 中添加以下配置并重新启动服务器即可应用。

```ini
op-permission-level=4
```

注：`op-permission-level`为BDS隐藏有效键，需手动添加 (`[需要验证]`：社区与BDS内置文档确认有效，但Minecraft Wiki未列为正式键)。

## 1.26.x 版本新增的其他配置

新版 BDS 的默认文件还包含以下配置 (默认文件中以 `#` 注释或常规键形式存在, 简幻欢面板场景一般不需要改动):

* `allow-outbound-script-debugging` / `allow-inbound-script-debugging` (默认 `false`) 与 `script-debugger-*` 系列: 脚本调试器 (VSCode Debugger) 连接相关配置。
* `script-watchdog-*` 系列: 脚本看门狗, 用于检测脚本卡顿/超内存。
* `diagnostics-capture-*` 系列: 诊断捕获会话。
* `disable-client-vibrant-visuals` (默认 `true`): 为 `true` 时服务器要求客户端使用次一级的图像设置而不是 Vibrant Visuals (灵动视觉效果)。
* `sentry-rate-limit-window` / `sentry-max-events-per-window`: 脚本错误上报 (Sentry) 的限流。
* `enable-profiler` / `enable-editor-network-metrics` / `convert-world-to-editor-project`: 性能分析与编辑器相关。

完整键表与官方注释请以 [Minecraft Wiki 的 server.properties 条目](https://minecraft.wiki/w/Server.properties) (BDS 1.26.x 默认文件) 与 BDS 压缩包内置文档为准。
