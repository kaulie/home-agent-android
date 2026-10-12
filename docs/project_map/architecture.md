# 服务架构

```
living-room-android (Console)
        │  HTTP
        ▼
  Brain :9527
    POST /api/v1/edge-register     roles: intent_source + runtime + endpoint
    POST /api/v1/edge-heartbeat    间隔 30000ms（BuildConfig）
    POST /api/v1/intent
    GET  /api/v1/intent_detail
    GET  /api/v1/assets/{id}/content
```

- 底栏「互动 · 系统 · 能力 · 实体 · 节点」
- 图只认 `presentation.asset_ref`
- 语音在本机转成中文后再 POST
- 默认 Brain：`http://brain.local:9527`；Cloud：`http://49.234.45.173:9527`

`app-v2` 同样登记 / 心跳 / 拉单，心跳间隔 15000ms，client hint `living-room-chromecast`。技能源码：

```
plugins/netease-music/android/*.kt
plugins/chromecast-display/android/*.kt
```

由 `app-v2/build.gradle.kts` 的 `java.srcDir` 编进该 module。`settings.gradle.kts` 已 `include` `:app`、`:app-v2`、`:living-room-android`。
