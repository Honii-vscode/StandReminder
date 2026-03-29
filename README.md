# Stand Reminder 站立提醒

> 随机间隔提醒你站立活动，保护颈椎和腰椎健康。支持 PWA 和 Android APK。

A simple PWA that reminds you to stand up and stretch at random intervals, preventing prolonged sitting health issues.

## ✨ 功能特性

- 🔀 **随机间隔**：工作/休息时间随机打乱，避免身体适应
- 🔔 **多种提醒方式**：振动 + 音效 + 通知提醒
- 📊 **每日统计**：统计今日完成周期和累计工作时长，数据保存在本地
- 📱 **PWA 支持**：可安装到桌面，像原生应用一样使用
- 🤖 **Android 原生应用**：使用 Capacitor 打包，可以编译成 APK 安装到手机
- 🎨 **深色主题**：美观深色界面，省电护眼

## 📁 项目结构

```text
.
├─ public/
│  ├─ index.html      # 主应用（单文件包含所有 HTML/CSS/JS）
│  ├─ manifest.json   # PWA 应用清单
│  └─ sw.js           # Service Worker 离线缓存
├─ android/           # Capacitor Android 项目
├─ server.js          # Express 静态文件服务器
├─ package.json       # NPM 依赖配置
└─ capacitor.config.json  # Capacitor 配置
```

## 📋 环境要求

- Node.js 20+

## 🚀 本地运行

```bash
# 安装依赖
npm install

# 启动本地服务器
npm start
```

服务默认配置：
- 访问地址：`http://127.0.0.1:3001`
- 仅允许本地访问

### 允许局域网访问

```bash
npm run start:public
```

服务绑定到 `0.0.0.0:3001`，同一局域网内其他设备可以访问。

## 🤖 打包 Android APK

本项目使用 [Capacitor](https://capacitorjs.com/) 打包成原生 Android 应用。

### 前置条件

- Android SDK (Android Studio 或命令行工具)
- JDK 17+
- 配置好 `ANDROID_HOME` 环境变量

### 构建步骤

```bash
# 安装依赖
npm install

# 同步 Web 资源到 Android 项目
npx cap sync android

# 构建调试 APK
cd android
./gradlew assembleDebug
```

生成的 APK 位置：
```
android/app/build/outputs/apk/debug/app-debug.apk
```

### 构建发布版 APK

```bash
./gradlew assembleRelease
```

## 🔐 Android 权限说明

| 权限 | 用途 |
|------|------|
| `VIBRATE` | 提醒时振动 |
| `WAKE_LOCK` | 保持后台计时准确 |
| `POST_NOTIFICATIONS` | 显示通知提醒 (Android 13+) |
| `INTERNET` | 网络访问 |

## 🔧 调试

- 打开网页时添加 `?debug=1` 参数启用调试面板
- 或在控制台执行 `localStorage.setItem('standReminderDebug', '1')`
- 调试面板显示当前状态、剩余时间、可见性变化等信息

## 🔒 安全说明

- 只提供 `public/` 目录下的静态文件访问
- 不要将敏感信息存放在此仓库中
- 生产环境请使用 HTTPS

## 📄 许可证

MIT
