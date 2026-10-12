# 技术栈

| 项 | 事实 |
|---|---|
| 语言 | Kotlin |
| UI（Console） | Jetpack Compose（`org.jetbrains.kotlin.plugin.compose`） |
| UI（app-v2） | AppCompat + Leanback |
| 构建 | Gradle Kotlin DSL，仓根 `./gradlew` |
| compileSdk / targetSdk | 35 |
| Java / JVM | 17 |
| Console minSdk | 26；versionCode 6；versionName `0.6.0-console` |
| app-v2 minSdk | 24；versionCode 3；versionName `0.5.0` |
| 网络 | OkHttp（app-v2）；Console 以该 module 依赖为准 |
| 相机 | CameraX（Console） |
| 扫描 | ML Kit Document Scanner（需 Play 服务） |

无 `build.sh`。无 Docker。不要依赖 os 的 `../plugins/`。
