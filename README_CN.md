# Claude JSONL History Viewer

一个用于浏览 Claude Code 对话历史的单文件 Web 应用程序。该应用提供了可视化界面，用于探索 Claude AI 对话，包括用户消息、助手回复、工具调用和元数据。

> [English Documentation](README.md) | 中文文档

## 特性

### 🎯 核心功能
- **单文件应用**: 无需构建过程，直接在浏览器中打开 HTML 文件即可使用,无任何外部依赖的 CSS
- **文件系统访问**: 使用现代浏览器 File System Access API 读取本地目录和 JSONL 文件
- **多语言支持**: 完整的中英文界面切换 

### 📊 数据解析
- **JSONL 格式支持**: 解析标准的 Claude 对话 JSONL 格式
- **会话分组**: 按 sessionId 自动分组对话会话
- **消息类型识别**: 支持用户、助手、系统、总结等多种消息类型
- **工具调用可视化**: 特殊处理常见工具（TodoWrite、Edit、MultiEdit 等）

### 🎨 界面特色
- **文件树导航**: 可折叠的项目结构浏览
- **消息颜色编码**: 不同类型消息使用不同颜色标识
- **语法高亮**: JSON 数据语法高亮显示
- **文本对比**: 支持 Edit/MultiEdit 工具的文本差异对比
- **待办事项渲染**: TodoWrite 工具的可视化展示

## 快速开始

### 使用方法
1. **打开应用**: 下载到本地后，直接在浏览器中打开 `claude-code-history-viewer.html` 
2. **选择目录**: 点击"选择"按钮，选择包含 Claude JSONL 文件的项目文件夹
3. **浏览对话**: 在左侧文件树中点击 JSONL 文件，右侧将显示对话详情

### 浏览器要求
- **Chrome 86+** 或 **Edge 86+**（推荐）
- 需要支持 File System Access API
- 不支持 Safari 和 Firefox（API 支持有限）


### 架构设计

#### 组件架构
- **ClaudeCodeHistoryApp**: 主应用容器，管理整体布局和状态
- **DataManager**: 中央数据管理，包含 IndexedDB 持久化
- **StyleManager**: 集中式样式管理，嵌入 Tailwind CSS
- **FileBrowser**: 文件树导航组件
- **MessageViewer**: 对话显示组件
- **LanguageManager**: 多语言管理组件

#### 核心功能
- **目录遍历**: 递归扫描项目目录结构
- **JSONL 解析**: 会话分组和消息提取
- **内容提取**: 不同类型消息的内容处理
- **工具渲染**: 特殊工具的可视化展示
- **数据持久化**: 使用 IndexedDB 保存目录句柄

## 技术特性

### 国际化支持
- 中英文翻译
- 自动检测浏览器语言
- 动态语言切换

### 性能优化
- 异步文件预览加载
- 增量式 JSONL 解析
- 非阻塞 IndexedDB 操作
- 嵌入式 CSS 避免外部依赖

### 安全考虑
- HTML 内容转义防止 XSS 攻击
- 文件访问权限管理
- 数据本地存储，不上传服务器

## 开发说明

### 自定义开发
如需扩展功能，主要关注以下组件：
- **DataManager**: 添加新的数据解析逻辑
- **MessageViewer**: 添加新的渲染组件
- **LanguageManager**: 添加新的翻译文本
- **StyleManager**: 添加新的样式定义

### 测试方法
- 直接在浏览器中打开 HTML 文件测试
- 使用真实的 Claude JSONL 文件进行验证
- 检查浏览器控制台是否有错误信息

## 许可证

本项目仅供学习和研究使用。

## 贡献

欢迎提交问题和改进建议！

---

**注意**: 本项目需要现代浏览器支持，请确保使用 Chrome 86+ 或 Edge 86+ 版本以获得最佳体验。