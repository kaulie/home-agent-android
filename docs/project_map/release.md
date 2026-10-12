# 发布细节

无 `build.sh`、无平台 `outputs/`、无 `deploy-notify`。

「发布」= 合入 `main` 之后，由人用 Gradle 打指定 variant 并安装。合入 `main` ≠ 用户设备已更新。

`local.properties`、keystore、`google-services.json` 不进 git，也不进「发版说明」当可拷贝的密钥。
