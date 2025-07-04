# Electron桌面应用配置规范

本文档定义了Electron桌面应用生成器的配置规范，用于生成跨平台桌面应用。

## 配置文件结构

配置文件采用JSON格式，命名为 `electron-config.json`。主要包含以下几个部分：

1. **app** - 应用基础信息
2. **window** - 窗口配置
3. **frontend** - 前端技术栈
4. **features** - 功能特性
5. **build** - 构建配置
6. **security** - 安全配置

## 完整配置示例

```json
{
  "app": {
    "name": "MyDesktopApp",
    "displayName": "我的桌面应用",
    "version": "1.0.0",
    "description": "基于Electron的跨平台桌面应用",
    "author": "开发者名称",
    "homepage": "https://myapp.com",
    "license": "MIT",
    "keywords": ["electron", "desktop", "app"],
    "category": "productivity"
  },
  "window": {
    "width": 1200,
    "height": 800,
    "minWidth": 800,
    "minHeight": 600,
    "maxWidth": 1920,
    "maxHeight": 1080,
    "resizable": true,
    "minimizable": true,
    "maximizable": true,
    "closable": true,
    "alwaysOnTop": false,
    "fullscreen": false,
    "kiosk": false,
    "titleBarStyle": "default",
    "frame": true,
    "transparent": false,
    "opacity": 1.0,
    "backgroundColor": "#ffffff",
    "show": true,
    "center": true,
    "focusable": true,
    "skipTaskbar": false,
    "icon": "assets/icon.png",
    "title": "我的桌面应用"
  },
  "frontend": {
    "framework": "react",
    "language": "typescript",
    "bundler": "webpack",
    "styling": "scss",
    "uiLibrary": "antd",
    "stateManagement": "zustand",
    "routing": "react-router"
  },
  "features": {
    "menu": {
      "enabled": true,
      "type": "application",
      "customMenu": true
    },
    "tray": {
      "enabled": false,
      "icon": "assets/tray-icon.png",
      "tooltip": "我的应用"
    },
    "autoUpdater": {
      "enabled": true,
      "provider": "github",
      "publisherName": "MyCompany"
    },
    "fileAssociation": {
      "enabled": true,
      "extensions": ["txt", "md", "json"],
      "name": "MyApp Document",
      "description": "MyApp支持的文档格式"
    },
    "protocolHandling": {
      "enabled": false,
      "schemes": ["myapp"]
    },
    "notifications": {
      "enabled": true,
      "sound": true
    },
    "clipboard": {
      "enabled": true,
      "watchChanges": false
    },
    "globalShortcuts": {
      "enabled": true,
      "shortcuts": [
        {
          "accelerator": "CmdOrCtrl+Shift+D",
          "action": "toggleDevTools"
        }
      ]
    },
    "powerMonitor": {
      "enabled": false,
      "events": ["suspend", "resume", "shutdown"]
    },
    "systemIdle": {
      "enabled": false,
      "threshold": 60
    },
    "crashReporter": {
      "enabled": true,
      "submitURL": "https://api.myapp.com/crash-reports"
    }
  },
  "build": {
    "appId": "com.mycompany.myapp",
    "productName": "MyApp",
    "directories": {
      "output": "dist",
      "buildResources": "build"
    },
    "files": [
      "dist/**/*",
      "node_modules/**/*",
      "package.json"
    ],
    "extraResources": [
      "assets/**/*"
    ],
    "asar": true,
    "compression": "maximum",
    "nsis": {
      "oneClick": false,
      "allowElevation": true,
      "allowToChangeInstallationDirectory": true,
      "installerIcon": "assets/installer-icon.ico",
      "uninstallerIcon": "assets/uninstaller-icon.ico",
      "installerHeaderIcon": "assets/installer-header-icon.ico",
      "createDesktopShortcut": true,
      "createStartMenuShortcut": true,
      "shortcutName": "MyApp"
    },
    "mac": {
      "category": "public.app-category.productivity",
      "icon": "assets/icon.icns",
      "hardenedRuntime": true,
      "gatekeeperAssess": false,
      "entitlements": "assets/entitlements.mac.plist",
      "entitlementsInherit": "assets/entitlements.mac.plist",
      "notarize": {
        "teamId": "TEAM_ID"
      }
    },
    "win": {
      "target": "nsis",
      "icon": "assets/icon.ico",
      "requestedExecutionLevel": "asInvoker",
      "certificateFile": "cert.p12",
      "certificatePassword": "password"
    },
    "linux": {
      "target": [
        "AppImage",
        "deb",
        "rpm"
      ],
      "icon": "assets/icon.png",
      "category": "Office",
      "desktop": {
        "Name": "MyApp",
        "Comment": "我的桌面应用",
        "Icon": "myapp",
        "Type": "Application",
        "Terminal": false,
        "MimeType": "text/plain;text/markdown;"
      }
    },
    "publish": {
      "provider": "github",
      "owner": "mycompany",
      "repo": "myapp",
      "private": false,
      "releaseType": "release"
    }
  },
  "security": {
    "nodeIntegration": false,
    "contextIsolation": true,
    "enableRemoteModule": false,
    "webSecurity": true,
    "allowRunningInsecureContent": false,
    "experimentalFeatures": false,
    "navigateOnDragDrop": false,
    "preload": "src/preload.ts",
    "sandbox": false,
    "csp": {
      "enabled": true,
      "policy": "default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'"
    },
    "permissions": {
      "camera": false,
      "microphone": false,
      "geolocation": false,
      "notifications": true,
      "persistentStorage": true,
      "fullscreen": true,
      "openExternal": true,
      "media": true
    }
  },
  "development": {
    "devTools": true,
    "hotReload": true,
    "devServerPort": 3000,
    "electronPort": 3001,
    "inspectPort": 5858
  },
  "database": {
    "enabled": false,
    "type": "sqlite",
    "path": "data/app.db",
    "migrations": true,
    "backup": true
  },
  "logging": {
    "enabled": true,
    "level": "info",
    "console": true,
    "file": true,
    "path": "logs/app.log",
    "maxFiles": 7,
    "maxSize": "10MB"
  },
  "analytics": {
    "enabled": false,
    "provider": "google",
    "trackingId": "UA-XXXXXXXX-X",
    "anonymizeIP": true,
    "collectUsageData": false
  },
  "localization": {
    "enabled": false,
    "defaultLocale": "zh-CN",
    "supportedLocales": ["zh-CN", "en-US", "ja-JP"],
    "fallbackLocale": "en-US",
    "loadPath": "locales/{{lng}}/{{ns}}.json"
  },
  "plugins": {
    "enabled": false,
    "directory": "plugins",
    "autoLoad": true,
    "sandboxed": true
  },
  "themes": {
    "enabled": true,
    "defaultTheme": "light",
    "supportedThemes": ["light", "dark", "auto"],
    "customThemes": false,
    "themeDirectory": "themes"
  }
}
```

## 配置字段说明

### app (必需)
应用基础信息配置

| 字段 | 类型 | 必需 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | - | 应用名称（英文，用于包名） |
| displayName | string | 是 | - | 应用显示名称 |
| version | string | 是 | "1.0.0" | 应用版本号 |
| description | string | 否 | - | 应用描述 |
| author | string | 否 | - | 作者信息 |
| homepage | string | 否 | - | 应用官网 |
| license | string | 否 | "MIT" | 许可证 |
| keywords | array | 否 | [] | 关键词 |
| category | string | 否 | "productivity" | 应用分类 |

### window (必需)
窗口配置

| 字段 | 类型 | 必需 | 默认值 | 说明 |
|------|------|------|--------|------|
| width | number | 是 | 1200 | 窗口宽度 |
| height | number | 是 | 800 | 窗口高度 |
| minWidth | number | 否 | 400 | 最小宽度 |
| minHeight | number | 否 | 300 | 最小高度 |
| maxWidth | number | 否 | - | 最大宽度 |
| maxHeight | number | 否 | - | 最大高度 |
| resizable | boolean | 否 | true | 是否可调整大小 |
| minimizable | boolean | 否 | true | 是否可最小化 |
| maximizable | boolean | 否 | true | 是否可最大化 |
| closable | boolean | 否 | true | 是否可关闭 |
| alwaysOnTop | boolean | 否 | false | 是否总在最前 |
| fullscreen | boolean | 否 | false | 是否全屏 |
| kiosk | boolean | 否 | false | 是否kiosk模式 |
| titleBarStyle | string | 否 | "default" | 标题栏样式 |
| frame | boolean | 否 | true | 是否显示边框 |
| transparent | boolean | 否 | false | 是否透明 |
| opacity | number | 否 | 1.0 | 透明度 |
| backgroundColor | string | 否 | "#ffffff" | 背景色 |
| show | boolean | 否 | true | 是否显示 |
| center | boolean | 否 | true | 是否居中 |
| focusable | boolean | 否 | true | 是否可聚焦 |
| skipTaskbar | boolean | 否 | false | 是否跳过任务栏 |
| icon | string | 否 | - | 窗口图标 |
| title | string | 否 | - | 窗口标题 |

### frontend (必需)
前端技术栈配置

| 字段 | 类型 | 必需 | 默认值 | 可选值 | 说明 |
|------|------|------|--------|--------|------|
| framework | string | 是 | "react" | "react", "vue", "svelte", "angular" | 前端框架 |
| language | string | 是 | "typescript" | "typescript", "javascript" | 开发语言 |
| bundler | string | 否 | "webpack" | "webpack", "vite", "rollup" | 构建工具 |
| styling | string | 否 | "scss" | "scss", "css", "less", "stylus" | 样式语言 |
| uiLibrary | string | 否 | "antd" | "antd", "mui", "chakra", "element-plus" | UI组件库 |
| stateManagement | string | 否 | "zustand" | "zustand", "redux", "mobx", "vuex", "pinia" | 状态管理 |
| routing | string | 否 | "react-router" | "react-router", "vue-router", "svelte-spa-router" | 路由管理 |

### features (可选)
功能特性配置

#### menu
应用菜单配置

| 字段 | 类型 | 必需 | 默认值 | 说明 |
|------|------|------|--------|------|
| enabled | boolean | 否 | true | 是否启用菜单 |
| type | string | 否 | "application" | 菜单类型 |
| customMenu | boolean | 否 | false | 是否自定义菜单 |

#### tray
系统托盘配置

| 字段 | 类型 | 必需 | 默认值 | 说明 |
|------|------|------|--------|------|
| enabled | boolean | 否 | false | 是否启用托盘 |
| icon | string | 否 | - | 托盘图标 |
| tooltip | string | 否 | - | 托盘提示 |

#### autoUpdater
自动更新配置

| 字段 | 类型 | 必需 | 默认值 | 说明 |
|------|------|------|--------|------|
| enabled | boolean | 否 | true | 是否启用自动更新 |
| provider | string | 否 | "github" | 更新提供商 |
| publisherName | string | 否 | - | 发布者名称 |

#### fileAssociation
文件关联配置

| 字段 | 类型 | 必需 | 默认值 | 说明 |
|------|------|------|--------|------|
| enabled | boolean | 否 | false | 是否启用文件关联 |
| extensions | array | 否 | [] | 支持的文件扩展名 |
| name | string | 否 | - | 文件类型名称 |
| description | string | 否 | - | 文件类型描述 |

### build (可选)
构建配置

| 字段 | 类型 | 必需 | 默认值 | 说明 |
|------|------|------|--------|------|
| appId | string | 是 | - | 应用ID |
| productName | string | 否 | - | 产品名称 |
| directories | object | 否 | - | 目录配置 |
| files | array | 否 | - | 包含的文件 |
| extraResources | array | 否 | - | 额外资源 |
| asar | boolean | 否 | true | 是否使用asar |
| compression | string | 否 | "normal" | 压缩级别 |

### security (可选)
安全配置

| 字段 | 类型 | 必需 | 默认值 | 说明 |
|------|------|------|--------|------|
| nodeIntegration | boolean | 否 | false | 是否启用Node集成 |
| contextIsolation | boolean | 否 | true | 是否启用上下文隔离 |
| enableRemoteModule | boolean | 否 | false | 是否启用远程模块 |
| webSecurity | boolean | 否 | true | 是否启用Web安全 |
| preload | string | 否 | - | 预加载脚本路径 |
| sandbox | boolean | 否 | false | 是否启用沙箱 |

## 应用类型模板

### 文本编辑器
适用于代码编辑器、富文本编辑器等文本处理应用

```json
{
  "app": {
    "name": "TextEditor",
    "category": "productivity"
  },
  "window": {
    "width": 1200,
    "height": 800,
    "minWidth": 600,
    "minHeight": 400
  },
  "frontend": {
    "framework": "react",
    "language": "typescript",
    "uiLibrary": "antd"
  },
  "features": {
    "menu": {
      "enabled": true,
      "customMenu": true
    },
    "fileAssociation": {
      "enabled": true,
      "extensions": ["txt", "md", "js", "ts", "json"]
    }
  }
}
```

### 音乐播放器
适用于音频播放、音乐管理等多媒体应用

```json
{
  "app": {
    "name": "MusicPlayer",
    "category": "entertainment"
  },
  "window": {
    "width": 1000,
    "height": 600,
    "minWidth": 800,
    "minHeight": 500
  },
  "frontend": {
    "framework": "vue",
    "language": "typescript",
    "uiLibrary": "element-plus"
  },
  "features": {
    "tray": {
      "enabled": true,
      "icon": "assets/music-icon.png"
    },
    "fileAssociation": {
      "enabled": true,
      "extensions": ["mp3", "flac", "wav", "ogg"]
    },
    "globalShortcuts": {
      "enabled": true,
      "shortcuts": [
        {
          "accelerator": "MediaPlayPause",
          "action": "togglePlay"
        }
      ]
    }
  }
}
```

### 系统监控工具
适用于系统监控、性能分析等工具类应用

```json
{
  "app": {
    "name": "SystemMonitor",
    "category": "utilities"
  },
  "window": {
    "width": 1400,
    "height": 900,
    "minWidth": 1000,
    "minHeight": 600
  },
  "frontend": {
    "framework": "react",
    "language": "typescript",
    "uiLibrary": "antd"
  },
  "features": {
    "alwaysOnTop": true,
    "powerMonitor": {
      "enabled": true,
      "events": ["suspend", "resume"]
    },
    "notifications": {
      "enabled": true,
      "sound": true
    }
  }
}
```

## 验证规则

1. **必需字段验证**：`app.name`、`app.displayName`、`app.version`、`window.width`、`window.height`、`frontend.framework`、`frontend.language` 必须提供
2. **类型验证**：所有字段必须符合指定的数据类型
3. **枚举验证**：枚举类型字段必须使用预定义的值
4. **依赖验证**：某些功能之间存在依赖关系，需要一起启用
5. **平台兼容性**：某些功能仅在特定平台上可用
6. **版本格式**：版本号必须符合语义化版本规范

## 最佳实践

1. **安全优先**：始终启用 `contextIsolation` 和 `webSecurity`
2. **性能优化**：合理设置窗口大小和资源加载
3. **用户体验**：提供合适的菜单和快捷键
4. **跨平台兼容**：考虑不同平台的特性和限制
5. **自动更新**：为发布版本启用自动更新功能
6. **错误处理**：配置崩溃报告和日志记录
7. **国际化**：支持多语言的应用应启用本地化
8. **主题支持**：现代应用应支持明暗主题切换

## 示例配置文件

完整的示例配置文件可在 `examples/` 目录中找到：

- `examples/text-editor-app/electron-config.json` - 文本编辑器配置
- `examples/music-player-app/electron-config.json` - 音乐播放器配置
- `examples/system-monitor-app/electron-config.json` - 系统监控工具配置

## 配置验证

使用 JSON Schema 验证配置文件：

```bash
# 安装验证工具
npm install -g ajv-cli

# 验证配置文件
ajv validate -s schemas/electron-config.schema.json -d electron-config.json
```

配置文件必须通过 Schema 验证才能用于生成 Electron 应用。