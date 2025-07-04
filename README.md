# 🖥️ Electron桌面应用生成器

> AI驱动的跨平台桌面应用生成工具，让非程序员也能快速创建专业的桌面应用

## 📋 复制AI提示词开始使用

```prompt
你好！我想创建一个跨平台桌面应用，请帮我生成完整的Electron项目代码。

作为Electron专家开发者，请按照以下步骤进行：

1. **理解需求**：首先询问我的应用类型和主要功能需求

2. **配置生成**：根据我的需求，创建electron-config.json配置文件，遵循以下规范：
   - 参考：https://github.com/vibetemplate/desktop-generator/blob/main/ELECTRON-SPEC.md
   - 验证：https://github.com/vibetemplate/desktop-generator/blob/main/schemas/electron-config.schema.json

3. **代码实现**：基于配置文件生成完整的项目，包括：
   - 现代化Electron主进程架构 (最新版本)
   - React/Vue渲染进程界面
   - TypeScript类型安全
   - 原生菜单和系统集成
   - 打包配置(Windows/macOS/Linux)
   - 自动更新机制
   - 安全策略配置

4. **参考示例**：
   - 文本编辑器：https://github.com/vibetemplate/desktop-generator/tree/main/examples/text-editor-app
   - 音乐播放器：https://github.com/vibetemplate/desktop-generator/tree/main/examples/music-player-app  
   - 系统监控工具：https://github.com/vibetemplate/desktop-generator/tree/main/examples/system-monitor-app

5. **组件模板**：使用预设组件加速开发：
   - https://github.com/vibetemplate/desktop-generator/tree/main/templates

请开始询问我的具体需求吧！
```

## 🚀 快速开始

### 方式一：AI工具生成（推荐）

1. 复制上面的提示词
2. 粘贴到AI工具（Cursor、Claude Code、ChatGPT等）
3. 描述你的桌面应用需求
4. 获得完整的Electron项目代码

### 方式二：手动配置

1. 克隆项目
```bash
git clone https://github.com/vibetemplate/desktop-generator.git
cd desktop-generator
```

2. 查看配置规范
```bash
# 阅读配置文档
cat ELECTRON-SPEC.md

# 查看示例配置
ls examples/
```

3. 创建配置文件
```bash
# 复制示例配置
cp examples/text-editor-app/electron-config.json my-app-config.json

# 编辑配置
vim my-app-config.json
```

## 📁 项目结构

```
desktop-generator/
├── README.md                 # 本文档
├── ELECTRON-SPEC.md         # 配置规范文档
├── schemas/                 # JSON Schema验证
│   └── electron-config.schema.json
├── examples/               # 示例应用
│   ├── text-editor-app/    # 文本编辑器
│   ├── music-player-app/   # 音乐播放器
│   └── system-monitor-app/ # 系统监控
├── templates/              # 组件模板
│   ├── components/         # UI组件
│   ├── main/              # 主进程模板
│   └── renderer/          # 渲染进程模板
└── docs/                   # 文档
    ├── 快速开始.md
    ├── 配置指南.md
    └── 最佳实践.md
```

## 🎯 支持的应用类型

- **📝 文本编辑器** - 代码编辑器、富文本编辑器、Markdown编辑器
- **🎵 多媒体工具** - 音乐播放器、视频播放器、图片查看器
- **📊 数据工具** - 数据可视化、图表工具、数据库管理器
- **⚙️ 系统工具** - 系统监控、文件管理器、终端模拟器
- **🎮 游戏应用** - 小游戏、游戏启动器、模拟器
- **💼 办公工具** - 笔记应用、任务管理、计算器
- **🌐 网络工具** - API测试、网络监控、下载管理器

## 🛠️ 技术特性

### 现代化Electron架构
- **最新Electron版本** - 性能优化，安全增强
- **进程隔离** - 主进程与渲染进程分离
- **上下文隔离** - 安全的渲染进程环境
- **预加载脚本** - 安全的API暴露机制

### 跨平台支持
- **Windows** - .exe安装包，自动更新
- **macOS** - .dmg/.app，代码签名，公证
- **Linux** - .deb/.rpm/.AppImage

### 前端技术栈
- **React/Vue选择** - 现代化UI框架
- **TypeScript** - 类型安全开发
- **Webpack/Vite** - 模块化构建
- **SCSS/CSS Modules** - 样式管理

### 原生集成
- **系统菜单** - 原生菜单栏集成
- **系统托盘** - 后台运行支持
- **文件关联** - 文件类型关联
- **系统通知** - 原生通知支持
- **剪贴板** - 系统剪贴板操作
- **快捷键** - 全局快捷键支持

## 📊 配置示例

### 基础文本编辑器配置
```json
{
  "app": {
    "name": "SimpleEditor",
    "displayName": "简易编辑器",
    "version": "1.0.0",
    "description": "轻量级文本编辑器"
  },
  "window": {
    "width": 1200,
    "height": 800,
    "minWidth": 800,
    "minHeight": 600,
    "resizable": true
  },
  "frontend": {
    "framework": "react",
    "language": "typescript"
  },
  "features": {
    "menu": true,
    "tray": false,
    "autoUpdater": true,
    "fileAssociation": ["txt", "md"]
  }
}
```

## 🎨 组件库

### UI组件
- **TitleBar** - 自定义标题栏
- **MenuBar** - 应用菜单栏
- **StatusBar** - 状态栏
- **SidePanel** - 侧边栏
- **TabView** - 标签页容器
- **FileTree** - 文件树
- **CodeEditor** - 代码编辑器
- **MediaPlayer** - 媒体播放器

### 功能组件
- **FileManager** - 文件管理
- **SettingsPanel** - 设置面板
- **ThemeProvider** - 主题管理
- **ShortcutManager** - 快捷键管理
- **UpdateChecker** - 更新检查
- **WindowControls** - 窗口控制

## 📚 文档链接

- [配置规范文档](ELECTRON-SPEC.md)
- [快速开始指南](docs/快速开始.md)
- [配置完整指南](docs/配置指南.md)
- [开发最佳实践](docs/最佳实践.md)
- [组件使用文档](templates/README.md)

## 🔧 开发工具

### 验证配置
```bash
npm install -g ajv-cli
ajv validate -s schemas/electron-config.schema.json -d your-config.json
```

### 本地开发
```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建应用
npm run build

# 打包应用
npm run pack
```

## 📖 示例应用

### 1. 文本编辑器
功能齐全的文本编辑器，支持多标签页、语法高亮、文件管理。

**特性：**
- 多文件标签页
- 语法高亮
- 文件树导航
- 查找替换
- 主题切换

### 2. 音乐播放器  
现代化音乐播放器，支持多格式音频、播放列表管理。

**特性：**
- 音频播放控制
- 播放列表管理
- 音乐库浏览
- 均衡器
- 系统托盘集成

### 3. 系统监控工具
实时系统性能监控工具，显示CPU、内存、网络使用情况。

**特性：**
- 实时性能图表
- 进程管理
- 系统信息
- 性能警报
- 数据导出

## 🤝 贡献指南

1. Fork 项目
2. 创建功能分支
3. 提交更改
4. 推送到分支  
5. 创建 Pull Request

## 📄 许可证

MIT License - 查看 [LICENSE](LICENSE) 文件了解详情

## 🔗 相关项目

- [AI网站生成器](https://github.com/vibetemplate/ai-web-generator) - AI驱动的网站生成工具
- [小程序生成器](https://github.com/vibetemplate/miniprogram-generator) - uni-app跨平台小程序生成器

---

**让AI帮你快速构建专业桌面应用！** 🚀