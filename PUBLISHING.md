# 发布流程

本目录应作为单独的 GitHub 仓库初始化，例如 `carbon-element-video-releases`。它与当前私有源码仓库没有自动同步关系。

## 首次创建

1. 在 GitHub 创建公开仓库 `carbon-element-video-releases`。
2. 将本目录中的文件复制到该仓库根目录并推送。
3. 上传真实应用图标和截图到 `assets/`。
4. 将仓库的 GitHub Pages 来源设为 `main` 分支根目录；`index.html` 即可成为公开介绍页。
5. 在 `app-info.json` 中填写 Pages 地址、隐私政策地址和公开支持邮箱。

## 每次发布

1. 修改主项目 `pubspec.yaml`：递增 `version`，例如 `2.0.1+3`。
2. 在主项目本地构建：

```powershell
.\scripts\package-android.ps1 -Target apk
```

3. 在输出目录计算校验值：

```powershell
Get-FileHash .\build\releases\carbon-element-video-v2.0.1+3.apk -Algorithm SHA256
```

4. 更新本仓库的 `app-info.json`、`CHANGELOG.md`：填写版本、构建号、发布日期、Release 标签和 SHA-256。
5. 将本仓库的文档修改推送到 GitHub。
6. 在 GitHub 的 Releases 页面创建标签 `v2.0.1+3`，上传 APK，粘贴对应更新日志后发布。
7. 将生成的 Release 下载链接填回 `app-info.json` 的 `downloadUrl`，再推送一次。

## 发布检查

- 使用一台未安装旧版本的 Android 设备安装 APK。
- 使用已安装旧版本的设备覆盖安装，确认升级和数据迁移正常。
- 验证包名、版本号、应用图标、原生启动页、登录、播放和基础接口。
- 确认 APK 的 SHA-256 与 Release 页面一致。
- 确认 README、静态页面和 `app-info.json` 中没有测试地址、密钥或本地路径。

## 后续自动化

稳定后可在私有源码仓库配置 GitHub Actions：推送 `v*` 标签后构建 APK，并通过一个仅拥有该发布仓库 Contents/Actions 写入权限的 Fine-grained Token 上传 Release。该 Token 仅保存在 GitHub Secrets，绝不写入 Flutter 配置、Android Gradle 文件或 Git 历史。
