# 项目定位

## 一句话

home-agent-android 是家庭 Agent 的 Android 客户端仓：只打 Brain HTTP。不是 Brain，不是 sidecar，声明不在本仓。

仓库：[`https://github.com/kaulie/home-agent-android`](https://github.com/kaulie/home-agent-android)  
Gradle 根项目名：`LivingRoomControl`

## 三套 application

| 目录 | applicationId | 职责 |
|---|---|---|
| `living-room-android` | `com.smarthome.livingroom_android` | **主 Console**：Intent Source + Endpoint + 本机 Runtime（扫描 / CameraX / 电话 / GoPro fallback） |
| `app-v2` | `com.smarthome.livingroom_v2` | 机顶盒 Edge：网易云 + Chromecast 投屏技能，后台心跳 |
| `app` | `com.smarthome.livingroom` | 旧客厅中控（未点名不要动） |

Console 主屏幕名：`HomeAgent Console`。最低系统 Android 8.0（API 26）。扫描依赖 Google Play 服务（ML Kit Document Scanner）。

iPhone 对端：[home-agent-ios](https://github.com/kaulie/home-agent-ios)。

## 它不是什么

| 不是 | 谁才是 |
|---|---|
| 规划 / 能力目录 | Brain + 集市 |
| iPhone App | home-agent-ios |
| MPEG-TS 直播 / 客厅灯 / 投电视（Console 本期） | iOS / Mac Edge 各自边界 |
| `:4220` 服务 | Brain / Gateway / 集市 |
