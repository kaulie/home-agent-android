# AGENT.md — 后续 Agent 对本仓库的说明与向导

你是来改 **home-agent-android** 的。先读本文，再按 [`README.md`](README.md) 与各 module README 展开理解。  
本仓没有 `project_map/`。这是 Android 客户端：**只打 Brain HTTP**。  
os 已归档；不要再往 os 的 `android/` 提交。

## 1. 对本项目的理解

| 你应建立的判断 | 展开阅读 |
|---|---|
| 主发出窗是 `:living-room-android`（HomeAgent Console）：Intent Source + Endpoint + 本机 Runtime（扫描 / CameraX / 电话 / GoPro fallback） | [README.md](README.md)、[living-room-android/README.md](living-room-android/README.md) |
| `:app-v2` 是机顶盒 Edge（网易云 + 投屏技能）；`:app` 是旧中控，不再当主发出窗 | [app-v2/README.md](app-v2/README.md) |
| `app-v2` 技能 Kotlin 在本仓 `plugins/*/android/`，**声明**仍在 marketplace | [plugins/README.md](plugins/README.md)、`app-v2/build.gradle.kts` 的 `sourceSets` |
| 不要依赖 os 的 `../plugins/`。不要把 Admin 塞进 Console | README |
| 不在 `:4220` 发版 | README 构建节 |

Runtime 会要求优先读根目录 `AGENT.md`。你正在读的就是那份。

## 2. 开工前清单

1. workspace origin 是 `https://github.com/kaulie/home-agent-android`。
2. 从最新 `main` 开 `feat|fix|chore/<简述>`。
3. 只改点名的 module；`settings.gradle.kts` 已 `include` 三套。
4. 有 SDK 时：`./gradlew :living-room-android:assembleDebug`（或对应 module）。
5. 不要改 `/Users/gaolei/runtime/**`。不要改 os。不要改 iOS 仓（除非任务点名）。

## 3. 滞后信息：有义务更新

`app-v2/build.gradle.kts` 若再出现 `${rootProject.projectDir}/../plugins`，必须改回本仓 `plugins/`。  
README 仍写 `cd android` 时改成仓根。

## 4. 与事实不符：必须提出异议，禁止默认处理

| 你看到的 | 你不该做的 | 你该做的 |
|---|---|---|
| 任务要求 Android 做 MPEG-TS 直播 / `light.set` / 投电视 | 从 iOS 抄进来 | 异议：本期边界见 living-room-android README |
| 任务要求改能力声明 | 只改 Kotlin 当目录 | 异议：声明在 marketplace；本仓 plugins 只是 app-v2 编译源 |
| 任务要求直推 `main` 或改 os | 照做 | 异议：走 PR；os 已归档 |

```
异议：<文档路径> 声称 <原句>
事实：<文件:符号 或 命令输出>
处理：<已改文档 / 已改代码 / 需要人决定>
```

## 5. 改动落点

| 要改的东西 | 去哪 |
|---|---|
| 主 Console UI / intent / CameraX | `living-room-android/` |
| 机顶盒 Edge / 心跳 / 拉单 | `app-v2/` |
| 网易云 / Chromecast 技能源码 | `plugins/netease-music/android/`、`plugins/chromecast-display/android/` |
| 旧中控 | `app/`（未点名不要动） |
| Gradle | 根 `settings.gradle.kts`、`build.gradle.kts` |
| 给后续 agent 的地图 | 本文 + README |

## 6. 交付

- 提交信息说清为什么。
- `git push -u origin HEAD`，`gh pr create`，回写 `prUrl`。
- APK 安装不是 `:4220` 发版；只听从 `goal` 与人的明确指令。

## 7. 安全

不要提交 `local.properties`、keystore、`google-services.json`、`.idea/`。
