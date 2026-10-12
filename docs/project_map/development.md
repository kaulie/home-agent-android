# 开发流程

origin：`https://github.com/kaulie/home-agent-android`。从最新 `origin/main` 开短命分支，PR 回 `main`。禁止直推 / force push `main`。

1. 先读 [`../../AGENT.md`](../../AGENT.md) 与本目录。
2. 只改点名的 module。
3. `app-v2/build.gradle.kts` 若再出现 `${rootProject.projectDir}/../plugins`，改回本仓 `plugins/`。
4. 有 SDK：`./gradlew :living-room-android:assembleDebug`（或对应 module）。
5. 不要从 iOS 抄 MPEG-TS / `light.set` / 投电视进 Console。
6. 不要只改 Kotlin 当能力目录；声明在 marketplace。
7. 不要改 iOS 仓，除非任务点名。未点名不要动 `:app`。

不要提交 `local.properties`、keystore、`google-services.json`、`.idea/`。
