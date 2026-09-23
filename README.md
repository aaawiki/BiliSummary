# BiliSummary - B站视频字幕抓取与 AI 总结浏览器扩展

<p align="center">
  <b>一键提取 B 站视频字幕，AI 智能分段提炼核心要点与大纲结构</b><br>
  原生支持 <b>Google Chrome</b>、<b>Microsoft Edge</b> 等主流 Chromium 内核浏览器
</p>

---

## ✨ 核心特性

- ⚡ **精准字幕提取**：自动解析 B 站视频（支持单P、多P列表、播放列表及番剧/纪录片播放页）的全部官方字幕与 AI 生成字幕。
- 🕒 **时间戳高亮同步**：字幕跟随视频播放实时高亮，点击任意时间戳直接跳转播放对应片段。
- 🧠 **双通道 AI 总结架构**：
  - **通道 1：DeepSeek 网页免 Key 模式（免费）**
    - 登录官方 [chat.deepseek.com](https://chat.deepseek.com) 即可直接调用，无需申请付费 API Key。
    - 内置 WebAssembly PoW 验证求解器，长文本分段自动总结与上下文串联。
  - **通道 2：通用 API 接口模式**
    - 兼容 OpenAI 格式标准接口，支持自定义填入 Endpoint 与 API Key。
    - 支持 DeepSeek-V3/R1、GPT-4o、Claude 3.5 Sonnet、Qwen、GLM 等各大主流大模型。
- 🎨 **现代双模外观**：支持暗色/亮色主题自由切换、自定义字体大小、行高与自动滚动。
- 📄 **一键导出**：支持总结内容一键复制、导出为 Markdown 文件。

---

## 🚀 安装指南

### 1. Microsoft Edge 浏览器
1. 在 Edge 地址栏输入 `edge://extensions` 并回车；
2. 打开页面左下角（或侧边栏）的 **「开发人员模式」**；
3. 点击顶部的 **「加载解压缩的扩展」**；
4. 选择本项目根文件夹即可完成安装。
> 详见专用指南：[EDGE_INSTALL.md](EDGE_INSTALL.md)

### 2. Google Chrome 浏览器
1. 在 Chrome 地址栏输入 `chrome://extensions` 并回车；
2. 开启右上角的 **「开发者模式」**；
3. 点击左上角的 **「加载已解压的扩展程序」**；
4. 选择本项目根文件夹即可。

---

## 🛠️ 技术架构

- **Manifest V3**：遵循现代浏览器最新扩展安全与权限标准（Service Worker + Content Scripts + Offscreen/MAIN world 脚本交互）。
- **WebAssembly**：内置 WASM PoW 计算模块，高效响应 DeepSeek 网页端防护校验。
- **SPA 路由监听**：采用 MutationObserver 动态响应 B 站单页应用的 URL 和分P切换，无感刷新字幕。

---

## 📁 目录结构

```
.
├── manifest.json         # 浏览器扩展清单配置文件 (Manifest V3)
├── background.js         # 后台 Service Worker 脚本（API 代理、Cookie 管理与跨域通信）
├── content.js            # 内容脚本入口（页面交互与浮动图标管理）
├── EDGE_INSTALL.md       # Microsoft Edge 浏览器详细安装与配置手册
├── css/
│   └── panel.css         # 字幕与总结抽屉面板样式
├── icons/                # 插件高分辨率图标集
├── js/
│   ├── api-ai.js         # 通用 OpenAI 兼容 API 通信模块
│   ├── chapter.js        # 视频章节划分模块
│   ├── deepseek.js       # DeepSeek 浏览器会话通信模块
│   ├── export.js         # Markdown 导出与剪贴板交互模块
│   ├── panel.js          # 面板 UI 渲染与事件监听中心
│   ├── prompt.js         # AI 结构化总结提示词模板
│   ├── settings.js       # 用户偏好与 API 配置存储模块
│   ├── state.js          # 全局状态管理
│   └── subtitle.js       # B 站字幕抓取、解析与播放器时间同步
└── libs/
    ├── deepseek-api.js    # DeepSeek 核心接口封装
    ├── deepseek-bridge.js # MAIN 与 ISOLATED 上下文消息桥接
    └── wasm-solver.js     # WebAssembly PoW 求解器
```

---

## 📄 开源许可证

本项目基于 [MIT License](LICENSE) 开源。
