# 部署细节

**不是** `:4220`。没有 runtime 目录。

```bash
./gradlew :living-room-android:assembleDebug
adb install -r living-room-android/build/outputs/apk/debug/living-room-android-debug.apk
```

其它 module 同理：`:app-v2:assembleDebug`、`:app:assembleDebug`。

APK 安装听从 `goal` 与人的明确指令。不要改 `/Users/gaolei/runtime/**`。不要改 os。
