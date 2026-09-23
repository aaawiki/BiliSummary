# BiliSummary - Microsoft Edge 浏览器安装与使用指南

**BiliSummary** 是一款 B 站视频字幕抓取与 AI 总结扩展。当前现代 Microsoft Edge 浏览器完全基于 **Chromium** 内核，原生完美兼容 Manifest V3 (MV3) 扩展标准。

---

## 🚀 快速安装（免商店，3步完成）

### 步骤 1：打开 Edge 扩展管理页面
在 Microsoft Edge 浏览器的地址栏输入以下地址并回车：
```
edge://extensions
```

### 步骤 2：开启「开发人员模式」
在扩展页面左侧边栏的底部，找到 **「开发人员模式」**（Developer Mode）开关，将其**开启**。
*(如果左侧栏折叠，请点击左上角的“三条杠”菜单展开)*

### 步骤 3：加载解压后的插件
1. 开启开发人员模式后，页面顶部会显现几个新按钮，点击 **「加载解压缩的扩展」**（Load unpacked）。
2. 在弹出的文件选择器中，选中当前插件文件夹（例如 `d:\bilisummary-v1.1.6-chrome`），点击 **「选择文件夹」**。
3. 扩展列表中即会出现 **BiliSummary**，状态为已启用。

---

## 📌 推荐使用设置

1. **固定到 Edge 工具栏**：
   - 点击 Edge 浏览器右上角的 **拼图形状「扩展」图标**；
   - 找到 **BiliSummary**，点击其右侧的 **「小眼睛」** 图标（在工具栏中显示按钮），即可将其固定在右上角。

2. **视频页面快速唤起**：
   - 打开任意 B 站视频页（如 `https://www.bilibili.com/video/BV...` 或番剧/剧集播放页）；
   - 视频右侧会自动出现 BiliSummary 的圆形浮动快捷按钮，点击即可展开/收起字幕与总结面板；
   - 也可以随时点击 Edge 右上角工具栏的插件图标唤起面板。

---

## 🤖 AI 总结通道配置

插件支持两种 AI 通道，可在面板右上角的「设置」中随时切换：

### 通道一：DeepSeek 浏览器免 Key 模式（推荐，免费）
- **特点**：无需申请付费 API Key，直接复用 DeepSeek 官方网页版算力；
- **配置方法**：
  1. 在 Edge 浏览器中新开标签页访问并登录 [chat.deepseek.com](https://chat.deepseek.com)；
  2. 回到 B 站视频页，点击 BiliSummary 面板中的「DeepSeek 浏览器通道」；
  3. 插件会自动利用会话完成字幕长文本分段与结构化总结。

### 通道二：自定义 API 接口模式
- **特点**：响应极速、稳定性高、支持各大主流大模型（DeepSeek-V3/R1、GPT-4o、Claude 3.5、Qwen 等）；
- **配置方法**：
  1. 打开 BiliSummary 面板右上角「设置」齿轮；
  2. 选择「自定义接口 (API)」；
  3. 填入 API Endpoint（例如 `https://api.deepseek.com/v1/chat/completions`）及对应的 API Key；
  4. 选择或输入模型名称（如 `deepseek-chat` 或 `deepseek-reasoner`），点击保存即可。

---

## ❓ 常见问题与排查

1. **提示“当前页面不是 B 站视频页”？**
   - 确认当前网页 URL 是否包含 `/video/BV...`、`/list/...` 或 `/bangumi/play/...`。
   - 刷新视频页面重试。

2. **提示“DeepSeek 未登录” 或 Edge 网页端无法登录 DeepSeek？**
   - **方案 A（最常见：Edge 跟踪预防拦截）**：
     Edge 默认启用了「平衡型跟踪预防」，可能会拦截 DeepSeek 登录时的 Cloudflare 验证码（Turnstile）或滑块验证。
     - 在 Edge 中打开 [chat.deepseek.com](https://chat.deepseek.com)；
     - 点击地址栏最左侧的 **「小锁」** 或 **「网站信息/盾牌」** 图标；
     - 找到 **「跟踪预防」**（Tracking Prevention），将其开关切换为 **「关」**；
     - 刷新页面后重新输入账号密码登录。
   - **方案 B（保持标签页打开）**：
     - 在 Edge 任意标签页打开并登录好 [chat.deepseek.com](https://chat.deepseek.com)，无需关闭该标签页；
     - 插件已升级支持直接从当前已打开的 DeepSeek 标签页快速同步 Token，瞬间识别登录状态。
   - **方案 C（关闭该站点睡眠）**：
     - 访问 `edge://settings/system`，在「从不将这些站点置于睡眠状态」中添加 `chat.deepseek.com`，防止 Edge 在后台挂起会话导致断开。

3. **Edge 重启后提示“请禁用开发人员模式扩展”？**
   - 这是 Chromium 浏览器的常规安全提示，点击右侧的关闭或“继续保持开启”即可，不会影响插件正常使用。

---

## 📦 打包提审 Edge 扩展商店（开发者可选）

如需将该插件发布至 **Microsoft Edge Add-ons 微软扩展商店**：
1. 运行根目录下的打包命令，将插件目录打包为 ZIP（排除 `.git`、说明文档等无关文件）；
2. 登录 [Microsoft 合作伙伴中心 (Partner Center)](https://partner.microsoft.com/dashboard/microsoftedge/overview)；
3. 创建新扩展，上传生成的 ZIP 压缩包；
4. 填写商店详情与权限声明即可提交审核。
