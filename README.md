# WW3 Air Combat AI（ww3ai）

给 McWW3 的无人战机装上会自己飞、会追人、会开火的服务端 AI。

适用环境：Minecraft 1.20.1 / Forge 47.4.29 / McWW3 2.1-beta。当前版本 `1.0.0`（build138）。

> **免责声明**：本项目为第三方扩展，与 McWW3 作者（Voy7、ChampPG）无隶属或授权关系。
> 本项目**不包含** McWW3 的任何代码、模型、音效或配置数据，发行 jar 内仅含 `com/ww3ai` 下的类，
> 仅在运行时通过其公开类接口协作。McWW3 的许可为 `All Rights Reserved`，不可再分发，
> 其下载与使用请遵守官方许可。Distant Horizons、Minecraft、Forge 同理，权利归各自所有者。

---

## 这个仓库有什么

| 路径 | 内容 |
| --- | --- |
| `mods/ww3ai-1.0.0.jar` | 可直接安装的 Mod 本体 |
| `docs/mod-guide.html` | **入口**：介绍 + 五分钟上手教程，单页、零外部依赖、断网可看 |
| `docs/MOD介绍与教程.md` | 同内容的 Markdown 版，可贴百科 / 论坛 |
| `docs/使用说明书.md` | 按「我要做什么」组织的操作手册，带命令总表与验证清单 |
| `docs/使用指南.md` | 原理、配置速查、故障排查、已知边界 |
| `docs/ww3-物理基线.md` | 飞行模型参数体系与标定方法 |
| `docs/BUILD.md` | 构建环境说明 |
| `LICENSE` | MIT，Copyright (c) 2026 moxiaomx114 |

**本仓库只发布可执行 jar 与文档，不含源码、不含构建脚本，也不含任何第三方模组二进制。**

---

## 前置依赖（需自行获取）

| 需要 | 版本 | 来源 |
| --- | --- | --- |
| Minecraft | 1.20.1 | 官方启动器 |
| Forge | 47.4.29（要求 `[47,)`） | Minecraft Forge 官方 |
| McWW3 | 2.1-beta | https://mcww3.com/download |
| Distant Horizons | 3.3.3 或兼容版本 | https://modrinth.com/mod/distanthorizons |

`ww3` 与 `distanthorizons` 是 `META-INF/mods.toml` 里的**强制依赖**，缺失会直接导致启动失败。
本仓库不提供这两项的下载，请按上面的官方渠道自行获取。

---

## 安装

1. 把 `mods/ww3ai-1.0.0.jar` 复制进游戏实例的 `mods/` 目录：
   - 普通实例：`.minecraft/mods/`
   - 版本隔离实例：`.minecraft/versions/<版本目录>/mods/`
   - **只放一份**：全局 `mods/` 与版本隔离 `mods/` 同时存在会触发 `Duplicate mod id`。
2. **完全退出启动器（PCL）再重新打开**。Forge 只在启动时加载 jar 与读配置，热替换不生效。
3. 首次启动会生成 `config/ww3ai-common.toml`，保持默认值即可运行。
4. 双击 `docs/mod-guide.html`，按「五分钟上手」逐条验证。

## 常用命令

| 命令 | 作用 |
| --- | --- |
| `/ww3ai deployer` | 拿手持部署器（选机型 / 队伍 / 位置，成批投放） |
| `/ww3ai status` | 看接管了哪些飞机、敌我编队与目标分配 |
| `/ww3ai diag` | 逐机遥测，排障第一入口 |
| `/ww3ai assign` | 把附近飞机编成自己的僚机队 |
| `/ww3ai doctrine` | 查看战后微调的战术参数 |

完整命令表见 `docs/使用说明书.md` 附录。

## 已知边界

- `flight.cruiseSpeed = 130` 是能量分档与保护阈值的**参考尺**，不是飞机能飞到的速度；油门 trim 由独立的 `flight.trimSpeed = 80` 控制。两者不是一回事，别把前者往下调。
- `flight.ratePGain` 默认 `0.60`；若杆抖动可小幅下调，反应迟钝再往回加，一次只改一个。
- Split-S / Wingover / Immelmann / Loop 的最低进入速度写死在 150–200 m/s，当前机型受气动阻力限制达不到，日志里的 `lease REVOKE reason=NO_MANEUVER` 属预期现象。
- McWW3 的阻力随速度平方增长而推力近似恒定，存在**气动极速**，不存在硬编码的 `maxSpeed`。
- 更多边界与排障见 `docs/使用指南.md`。

## 许可

本仓库中的 jar 与文档按 **MIT** 许可发布，详见 `LICENSE`。
MIT 允许自由使用、修改、再分发与商用，前提是保留版权声明与许可文本。

第三方组件（McWW3、Distant Horizons、Minecraft、Forge）不在本许可范围内。
