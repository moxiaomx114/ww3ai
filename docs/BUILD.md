# 构建说明

> **本发布仓库只含可执行 jar 与文档，不含源码与构建脚本。**
> 只是安装使用 Mod 的话，直接看 [`mod-guide.html`](mod-guide.html) 即可，不需要本文。
> 下文适用于「你在自己的源码工程里从零构建 ww3ai」的场景。

## 需要自行准备

| 需要 | 来源 | 放到 |
| --- | --- | --- |
| JDK 17 | 任意发行版 | 设好 `JAVA_HOME`，并把构建脚本里的路径改成你本机的实际路径 |
| Gradle 9.8.2 | https://mirrors.cloud.tencent.com/gradle/gradle-9.8.2-bin.zip | `tools/gradle-9.8.2/` |
| McWW3 2.1-beta | https://mcww3.com/download | `libs/` 与 `repo/ww3/ww3/2.1-beta/` |
| Distant Horizons 3.3.3 | https://modrinth.com/mod/distanthorizons | `libs/` |

> McWW3 为 `All Rights Reserved` 软件，不得随任何仓库再分发。
> 本工程仅在其**已安装于本地**的前提下于编译期引用，不随仓库分发。
> `repo/ww3/ww3/2.1-beta/` 下的 `.pom` 是工程自己写的坐标描述，可以保留。

## 构建

```bash
export JAVA_HOME=<你的 JDK 17 路径>
./build-direct.sh
```

产物：`build/libs/ww3ai-1.0.0.jar`。

两点经验：

1. **发行 jar 必须取构建链的 `renameJar` 产物**，不要用带 `-unobfuscated` 后缀的裸 jar。
   后者对 vanilla 方法的调用名没有对齐运行时环境，进游戏会 `NoSuchMethodError`。
2. **构建走直连脚本，不经过代理**；工具链统一使用 JDK 17 自带的版本，避免版本错配。

## 产出物校验

- 发行 jar 内应只有 `com/ww3ai` 下的类，不含任何第三方 class 或 `assets/ww3/` 资源。
- 不应包含 `fernflower_abstract_parameter_names.txt` 等反编译工具残留。
- `META-INF/mods.toml` 中的 `license` 与 `authors` 应与仓库顶层的 `LICENSE` 一致。
