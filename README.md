# home-agent-android

家庭 Agent 的 Android 客户端仓。只打 Brain HTTP（登记 / 心跳 / intent / asset），**不知道** sidecar 源码，也不 import Brain / Gateway。

源码从冻结的 [`home-agent-os/android`](https://github.com/kaulie/home-agent-os) 迁出；os 本身不再改这些 App。

iPhone 对端：[home-agent-ios](https://github.com/kaulie/home-agent-ios)。

## Modules

| 目录 | applicationId | 职责 |
|------|---------------|------|
| [living-room-android](living-room-android/) | `com.smarthome.livingroom_android` | **主 Console**：Intent Source + Endpoint + 本机 Runtime（扫描 / CameraX / 电话 / GoPro fallback） |
| [app-v2](app-v2/) | `com.smarthome.livingroom_v2` | Chromecast / 机顶盒 Edge：网易云 + 投屏技能，后台心跳 |
| [app](app/) | `com.smarthome.livingroom` | 旧客厅中控（不再当主发出窗） |

`app-v2` 编译需要的 Kotlin 技能源码在本仓 `plugins/*/android/`（从 os 插件树拷出）。能力**声明**仍在 [marketplace](https://github.com/kaulie/home-agent-capabilty-marketplace)。

## 构建主 Console

```bash
git clone https://github.com/kaulie/home-agent-android.git
cd home-agent-android
./gradlew :living-room-android:assembleDebug
adb install -r living-room-android/build/outputs/apk/debug/living-room-android-debug.apk
```

- 主屏幕名称：`HomeAgent Console`
- 最低系统：Android 8.0（API 26）
- 扫描依赖 Google Play 服务（ML Kit Document Scanner）

## Console 做什么

```text
启动 / 改 Brain URL
        │
 POST /api/v1/edge-register
   roles: intent_source + runtime + endpoint
        │
 POST /api/v1/edge-heartbeat
        │
 POST /api/v1/intent  →  GET /api/v1/intent_detail
```

- 底栏「互动 · 系统 · 能力 · 实体 · 节点」
- 图只认 `presentation.asset_ref`
- 语音在本机转成中文后再 POST

本期不做：MPEG-TS 直播、`light.set`、投电视、HomeAgent Admin。
