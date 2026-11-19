# WW3AI 空战模组

简体中文 · [English](README.en.md)

WW3AI 是 Minecraft 的 McWW3 附属模组。它让飞机自己飞、编队和交战。你可以叫一架僚机陪你飞，也可以在地图上摆好红蓝两队，看它们打一场。内置脚本可以直接用。想试语言模型时，再给队伍绑定模型。

本页对应中英双语版。游戏内的版本号仍显示 `1.0.0`。

[下载 WW3AI](https://github.com/moxiaomx114/ww3ai/releases) · [中英双语玩家手册](docs/WW3AI-Player-Manual-ZH-EN.pdf)

## 安装

这版在 **Minecraft Java 1.20.1、Forge 47.4.29 和 McWW3 2.1-beta** 上验证。还需要与 McWW3 配套的 Distant Horizons。

| 前置 | 获取方式 |
| --- | --- |
| Minecraft Java 1.20.1 | Minecraft 启动器 |
| Forge 47.4.29 | [Forge 下载页](https://files.minecraftforge.net/net/minecraftforge/forge/index_1.20.1.html) |
| McWW3 2.1-beta | [McWW3 下载页](https://mcww3.com/download) |
| Distant Horizons | [Modrinth](https://modrinth.com/mod/distanthorizons)，选与当前模组组合兼容的 Forge 版 |

1. 退出游戏，在 GitHub Releases 找到中英双语版，下载附件 **ww3ai-bilingual-tools.jar**。
2. 把 JAR 放进当前游戏实例的 `mods/` 文件夹。升级时先移出旧的 WW3AI JAR，每个实例只留一份。
3. 启动 Forge 实例，进世界后按 **G**。默认是简体中文，点控制台右上角的 **EN** 切成英文。

仓库中的 `mods/ww3ai-1.0.0.jar` 与这次发布的 `ww3ai-bilingual-tools.jar` 内容相同。

联机时，客户端和服务器请使用同一份 WW3AI 发布包。专用服务器的部分队伍和模型设置需要 OP 权限，批量部署器需要 OP 2。

## 进游戏先试这几个功能

| 想做什么 | 从哪里进 |
| --- | --- |
| 叫僚机或生成敌机 | 按 **G** 打开控制台。这里也能建队、改敌友关系、开关 AI 和开火。 |
| 改僚机命令和队形 | 按 **H** 轮换僚机命令，按 **J** 打开编队编辑并调整号位。 |
| 放一架飞机 | 从创造模式的「工具与实用物品」拿 **空战部署器**。认紫黑格图标。手持右键，选机型、队伍和武备，再到地图上选点。可交给 AI，也可停在地面自己开。 |
| 一次放多个小队 | 同一栏拿 **空战编队部署器**。每队选 1–5 架固定翼飞机，每批最多 8 个小队。可保存方案，也可确认后整批部署。 |

武备可以在空战部署器的「武备/蓝图」里存成蓝图。之后在批量部署器里，为同机型的小队选这份蓝图。

### 开一场 5v5

退出游戏或停服，在主机的 `config/ww3ai-common.toml` 的 `[general]` 下改两项，再启动。

    targetPlayersOnly = false
    maxVehicles = 12

默认上限是 8，5v5 至少需要 10 个空余 AI 名额。重新进世界，在 **G** 控制台打开 AI 和开火，把阵营设为「按 ww3 关系」。载入「双队 5v5」，检查两队的机位和高度，保持「阵营互敌」开启，再点「整批部署」。阵营互敌会改动这个世界里相关队伍的关系。

### 给不同队伍选模型

在 **G → 模型接入** 添加 OpenAI 兼容或 Ollama 渠道，获取模型列表，勾选所需模型并保存。启用渠道和模型总开关，再到 **G → 队伍控制**，选队伍、选「LLM 战术」和模型，点「应用到此队」。另一队单独设置。只想用内置规则时，选「纯脚本」。测试连接和模型请求可能产生服务商费用。

## 常用命令

| 命令 | 用途 |
| --- | --- |
| `/give @s ww3ai:deployer` | 拿空战部署器 |
| `/give @s ww3ai:batch_deployer` | 拿空战编队部署器 |
| `/ww3ai menu` | 打开控制台 |
| `/ww3ai status` | 查看 AI 状态 |

`/give` 需要作弊权限或 OP。完整操作步骤见上面的双语玩家手册。

遇到问题，请在 [Issues](https://github.com/moxiaomx114/ww3ai/issues) 附上游戏与模组版本、复现步骤和相关日志。贴日志前请移除 API Key 等凭据。

## 关于项目

这是 McWW3 的第三方扩展。主体由 hy4＋ds4.1f 开发，复核和改进由 gpt6.1sol 完成。仓库发布 WW3AI 的 JAR 和文档。WW3AI 按 [MIT](LICENSE) 许可发布，McWW3、Distant Horizons 等前置请从各自的发布渠道获取。
