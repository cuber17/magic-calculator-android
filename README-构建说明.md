# Magic Calculator Android

本工程将上游 `myhloli/magic-calculator` 的静态页面作为本地资产装入 Android WebView。
原页面的 HTML/CSS/JavaScript 和 `assets/image.png` 均保留；仅移除了页面中的百度统计远程脚本。
应用没有申请 INTERNET 权限，运行时不会加载原网站或请求在线资源。

## 兼容性目标

- `minSdk = 23`（Android 6.0 及以上）
- `compileSdk = 36`、`targetSdk = 36`
- Kotlin + Android WebView
- 横竖屏均可，由原网页 CSS 自适应
- 沉浸式全屏，隐藏系统状态栏和导航栏
- 无网络权限，网页资源从 APK 内 `file:///android_asset/` 加载

## 使用 Android Studio 构建 APK（Windows）

1. 安装最新版 Android Studio。
2. 在 SDK Manager 中安装 Android SDK Platform 36 和对应 Build-Tools。
3. 用 Android Studio 打开本文件夹 `MagicCalculatorAndroid`。
4. 等待 Gradle Sync 完成。
5. 选择菜单 **Build > Build Bundle(s) / APK(s) > Build APK(s)**。
6. Debug APK 输出位置：

   `app/build/outputs/apk/debug/app-debug.apk`

也可以在已配置 Android SDK、JDK 17+ 和 Gradle 的终端中运行：

- Windows：`build-apk.bat`
- macOS/Linux：`./build-apk.sh`

## 功能说明

原项目 README 所述的普通计算、魔术触发区、逐位修正数字、`2026=====` 隐藏配置口令、
0~60 秒缓冲阈值和目标时间计算逻辑均来自原始网页代码，没有在 Android 端重写。

## 重要验证说明

这是 Android Studio 工程，不是已经签名并在真机上验证过的 APK。
生成 APK 后，请至少在一台 Android 15/16 设备上检查显示比例、触摸拦截层、
普通四则运算、魔术模式和隐藏配置模式。不同厂商的 WebView 版本可能影响细节。

## 上游项目与许可

上游：https://github.com/myhloli/magic-calculator
上游采用 MIT License，原许可文件随工程保留于 `UPSTREAM-LICENSE`。
