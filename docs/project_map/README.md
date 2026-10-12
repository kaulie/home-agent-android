# project_map — home-agent-android 项目地图

本目录按**运行事实**说明本仓库，不是概念词典。

| 文档 | 维度 |
|---|---|
| [positioning.md](positioning.md) | 三套 module：Console / 机顶盒 / 旧中控 |
| [architecture.md](architecture.md) | Gradle、plugins 源码、Brain HTTP |
| [tech-stack.md](tech-stack.md) | Kotlin / Compose / Gradle |
| [deployment.md](deployment.md) | APK / adb，**不走 :4220** |
| [release.md](release.md) | 无 `build.sh` |
| [development.md](development.md) | 只改点名 module |

根目录 [`AGENT.md`](../../AGENT.md) 是后续 agent 的入口。各 module README 是细节。

## 本轮已核对的异议（2026-10-12）

1. **不在 `:4220` 发版。**
2. **主发出窗是 `:living-room-android`。** `:app` 是旧中控，不再当主发出窗。
3. **`app-v2` 技能 Kotlin 在本仓 `plugins/*/android/`。** `sourceSets` 必须指向 `${rootProject.projectDir}/plugins/...`，禁止再写 `../plugins`（那是 os 布局）。
4. **能力声明仍在 marketplace。** 本仓 plugins 只是 app-v2 编译源。
5. **本期 Console 不做** MPEG-TS 直播、`light.set`、投电视、HomeAgent Admin。
6. **README 构建命令从仓根跑 `./gradlew`**，不要写 `cd android`。
7. **minSdk：Console 26，app-v2 24。** versionName Console `0.6.0-console`。

后续 agent 若发现上述条目被新代码推翻，删除或改写。
