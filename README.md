# 高考志愿填报智能助手

这是一个基于Next.js框架开发的高考志愿填报智能助手Web应用，集成了WakaTime API进行编码时长统计，并接入QAnything大语言模型问答服务。

## 功能特点

- 智能问答：通过QAnything API提供专业的志愿填报建议
- 编码时长统计：集成WakaTime API，实时显示总编码时长
- 响应式设计：适配各种设备屏幕大小
- 现代UI：使用Tailwind CSS构建美观的用户界面

## 技术栈

- Next.js 14
- React 18
- TypeScript
- Tailwind CSS
- Axios
- Hero Icons
- React Markdown

## QAnything集成路径

本项目选择了路径二（API自行开发），主要原因如下：

1. 更好的用户体验：通过自定义UI和交互逻辑，提供更流畅的问答体验
2. 更高的可控性：可以自定义请求参数、错误处理和响应展示
3. 更强的扩展性：便于后续添加新功能，如上下文管理、历史记录等

实现细节：
- 创建专门的API路由处理QAnything请求
- 使用环境变量管理API密钥
- 实现流畅的对话界面
- 添加加载状态和错误处理

## WakaTime API集成

WakaTime API集成通过以下步骤实现：

1. 在环境变量中配置WakaTime API密钥
2. 创建Footer组件实时获取并显示编码时长
3. 使用useEffect hook定期更新数据
4. 优雅处理加载状态和错误情况

## 项目结构

```
src/
  ├── app/
  │   ├── api/
  │   │   ├── qa/
  │   │   │   └── route.ts    # QAnything API路由
  │   │   └── wakatime/
  │   │       └── route.ts    # WakaTime API路由
  │   ├── exercises/
  │   │   └── page.tsx        # 练习展示页面
  │   ├── qa/
  │   │   └── page.tsx        # 问答页面
  │   ├── layout.tsx          # 根布局
  │   └── page.tsx            # 首页
  ├── components/
  │   ├── exercises/
  │   │   ├── MockExercise.tsx        # 模拟填报练习
  │   │   ├── OptimizationAdvice.tsx  # 志愿优化建议
  │   │   ├── SchoolAnalysis.tsx      # 院校专业分析
  │   │   └── ScorePrediction.tsx     # 分数线预测
  │   ├── Header.tsx          # 头部导航
  │   ├── Footer.tsx          # 页脚（含WakaTime统计）
  │   └── QAChat.tsx          # 问答聊天组件
  └── styles/
      └── globals.css         # 全局样式
```

## 运行说明

1. 安装依赖：
```bash
npm install
```

2. 配置环境变量：
创建`.env.local`文件并添加以下配置：

```env
# QAnything API 配置
# 请在 QAnything 平台获取您的 API Key 和 Agent ID
# API Key 获取地址：https://ai.youdao.com/qanything/docs/intro/api-intro
QANYTHING_API_KEY=your_api_key_here
QANYTHING_AGENT_ID=your_agent_id_here

# WakaTime API 配置
WAKATIME_API_KEY=your_wakatime_api_key_here
```

### QAnything API 配置步骤：

1. 访问 [QAnything 平台](https://ai.youdao.com/qanything/docs/intro/api-intro)
2. 注册并登录您的账户
3. 在"个人账号-API 秘钥"中获取管理秘钥
4. 在"Agents-发布-API 秘钥"中获取问答秘钥
5. 创建或选择一个 Agent，获取 Agent ID
6. 将获取的 API Key 和 Agent ID 填入 `.env.local` 文件

### WakaTime API 配置步骤：

1. 访问 [WakaTime](https://wakatime.com/) 并注册账户
2. 在账户设置中生成 API Key
3. 将 API Key 填入 `.env.local` 文件

3. 启动开发服务器：
```bash
npm run dev
```

4. 访问 http://localhost:3000

## 功能模块

### 1. 智能问答 (/qa)
- 基于 QAnything API 的智能问答系统
- 支持高考志愿填报相关问题咨询
- 流畅的对话界面和实时响应

### 2. 练习展示 (/exercises)
- **模拟填报练习**：提供志愿填报的模拟练习环境
- **院校专业分析**：分析不同院校和专业的优劣势
- **分数线预测**：基于历史数据预测分数线趋势
- **志愿优化建议**：提供个性化的志愿填报建议

### 3. 首页 (/)
- 功能入口展示
- 项目介绍和导航

## 运行截图

[此处将添加实际运行截图]

## 注意事项

- 请确保正确配置所有环境变量
- QAnything API 需要有效的 API Key 和 Agent ID
- WakaTime API 密钥需要从 WakaTime 账户设置中获取
- 如果 QAnything API 调用失败，系统会自动使用备用回复

## 贡献指南

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建Pull Request

## 许可证

MIT License - 查看 [LICENSE](LICENSE) 文件了解详情 