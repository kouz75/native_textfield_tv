# Changelog

## [0.0.4] - 2026-11-22

### Android build compatibility
- Increase the plugin's `compileSdkVersion` from 33 to 34 to satisfy the API requirement of `androidx.fragment:fragment:1.7.1`.
- Update the Android Gradle Plugin to 8.11.1 and Kotlin to 2.2.20 in the plugin and example app.
- Update the example app's Gradle wrapper from 8.3 to 8.14.3 for compatibility with the installed Flutter SDK.
- Keep the plugin's minimum Android SDK at API 19.

### Validation
- Successfully build the example Android debug APK.
- Pass all 8 existing Flutter tests.

## [0.0.3] - 2025-07-26

### 版本更新
- 每个instance绑定到nativetextfiled而不是controller

## [0.0.2] - 2025-07-26

### 🚨 Critical Update - Android TV Remote Control Solution
- **Solves Flutter TextField TV Remote Issues**: This plugin addresses the critical problems described in [Flutter issue #154924](https://github.com/flutter/flutter/issues/154924) and [Flutter issue #147772](https://github.com/flutter/flutter/issues/147772) where Flutter's default TextField has multiple issues with TV remotes on Android TV devices
- **Native Android EditText**: Uses Android's native EditText component through PlatformView to ensure full TV remote compatibility
- **Perfect for Android TV Apps**: Specifically designed for apps that need text input on Android TV, Chromecast, Fire TV, and other TV devices

### 重要更新
- **NativeTextFieldController 现在继承自 TextEditingController**
  - 提供完整的 TextEditingController 兼容性
  - 支持同步文本操作（如 `controller.text = 'new text'`）
  - 支持监听器模式（`addListener` 和 `removeListener`）
  - 支持文本选择（`selection` 属性）
  - 支持 `clear()` 方法
  - 自动双向同步：Flutter 端和原生端的文本变化会自动同步

### 新增功能
- 支持在构造函数中设置初始文本：`NativeTextFieldController(text: '初始文本')`
- 支持所有 TextEditingController 的标准属性和方法
- 改进的文本同步机制，避免重复调用

### 兼容性
- 完全向后兼容，现有代码无需修改
- 可以在任何需要 TextEditingController 的地方使用 NativeTextFieldController

### 示例用法
```dart
// 创建控制器
final controller = NativeTextFieldController(text: '初始文本');

// 使用 TextEditingController 的功能
controller.text = '新文本';
controller.addListener(() {
  print('文本变化: ${controller.text}');
});
controller.clear();

// 使用原生功能
await controller.requestFocus();
await controller.setHint('新提示');
```

## [0.0.1] - 2024-01-XX

### 初始版本
- 基本的 NativeTextField 组件
- NativeTextFieldController 控制器
- Android 平台支持
- 焦点管理和文本操作
- 基本的文本变化和焦点变化监听
