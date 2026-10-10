# Simpfun_Wiki - 文档验证与优化工程契约 (2026-10-11)

## 目标

对 `https://github.com/Twelve-eight/Simpfun_Wiki`（Docusaurus 3.10.2 静态文档站，简幻欢社区维基）做全量检查、验证、优化，并扩充 Minecraft 文档知识面。信源优先级：

1. **实机证据**：本地 `G:\omp works\Minecraft\_runtime\versions\26.2-pre-5\server-26.2-pre-5.jar`（vanilla JE 服务端，可启动、可执行命令、可 dump 配置）。
2. **权威文档**：Minecraft Wiki（zh.minecraft.wiki）、Mojang 官方、Paper/Folia/Leaves 官方 docs、服务端核心官方源码/文档。
3. **本机无 Bedrock Dedicated Server 二进制** → BE 文档只能以官方文档 + 社区权威源核验，报告里必须标注"未实机验证"。
4. **Simpfun 平台自身行为**（面板 UI、套餐、价格、API）不可实机验证 → 只修事实错误与死链，不重写平台描述。

## 分支与工作区

- 工作分支：`main`（本地，跟踪 `origin/main`，已快进到 `40591af`）。
- 已停放现场：`opt/20260822-polish` 分支上 8 个未提交改动（README/EN 迁移声明 + 7 处相对链接修复）已 `git stash` 为 `wip-opt-polish-parked-20261011`。链接修复部分由本轮重写式落地；README 迁移声明不再恢复——本轮用户明确要求继续维护此仓库。
- 审查产物：`.review/2026-10-11/`（reports/ + tasks/），已加入 .gitignore，不进版本库。

## 代理规程（AGENTS.md Sec 4b / 8 / 8b 强制执行）

- 模型：用户指定 `devin-northstar/swe-2-max`（任务参数 `devin-northstar/swe-2-max:high`）。禁止自选替代。
- 并发 ≤8。每个子代理派发现场必须给出**唯一可写报告路径**（`.review/2026-10-11/reports/<name>.md`）。
- 子代理：首条结论立即增量写盘；每完成一个文件/检查面写一次；报告固定 `## 已确认 / ## 进行中 / ## 未知` 三段；不构建、不测试、不提交、不推送。
- 实现者与监督者**同批派发**；主会话 wait 实现者后通知监督者复核。
- 主会话职责：派发、收割报告、集中 `npm run build` 验证、git 提交推送、DEVLOG 记录。

## 内容规范

- 文档面向新手：中文、第二人称、步骤化；admonition 用 `::::tip|info|note|caution|warning|danger`（Docusaurus 语法）。
- 命令、路径、键名用 `` ` `` 包裹；表格对齐现有风格。
- **精确数值**：版本号、默认值、权限级别、端口范围必须来自实机或权威文档；不确定的标注 `[需要验证]` 而不是编造。
- 死链修复：相对链接 `./x.md` → `x.md`（同目录）；跨目录用相对路径而非 `/static` 绝对路径引用图片，与现有风格保持一致（现有混用 `../../static/img/...` 与 `<img src="/img/...">`，保留原样即可，只修 broken）。
- 不引入日语/韩语/阿拉伯语等非批准字符到任何输出。

## 验证门槛（交付前必须全部满足）

- `npm run build` 在 `main` 上 0 错误退出（onBrokenLinks/onBrokenMarkdownLinks = throw，构建即链接门禁）。
- 每个被改文档经监督者复核，报告留有"已确认"证据。
- 新增 gamerule/命令类内容至少有一处实机或官方文档引用。
- `git status` 干净；本地提交推送至 `origin/main`。

## 切片划分（审查 Phase 1，六只并行）

| 代理 | 范围 | 报告 |
|---|---|---|
| Rev-JE-Core | docs/mcje/20-serverproperties.md, 7-filestructure.md, 2-selectserver.md | rev-je-core.md |
| Rev-JE-FAQ | docs/mcje/1-JECommonQuestions/ + 100-motd, 5-addplugin, 6-AddMod, 8-playerdata, 25-Upload-worlds, 50-authlib-injector, 200-goodplugin, 201-goodmod, 500-customization | rev-je-faq.md |
| Rev-BE | docs/mcbe/ 全部 13 文件 | rev-mcbe.md |
| Rev-SFE | docs/0-main,1-register,5-recommend,7-signin,8-joinqqpd,9-commonsense,10-createserver,11-upload,12-unzip,15-reinstall,20-addport,25-backup,30-sftp,100-howtoask | rev-sfe.md |
| Rev-Other | docs/custom, PalWorld, RustedWarfare, mdt, tmod, blog/ | rev-other.md |
| Rev-Site | docusaurus.config.js, sidebars.js, src/, static/MinecraftBat.html, README.md, EN.md, vercel.json, ci.yml, 全库图片引用完整性 | rev-site.md |
