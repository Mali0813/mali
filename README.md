# 课程作业展示与AI助手系统

基于Next.js开发的个人课程作业展示平台，集成了WakaTime编码时间统计和QAnything AI问答功能。

## 功能特性

- 课程练习展示
  - 独立路由展示每个练习
  - 组件化开发
  - 响应式设计
- WakaTime API集成
  - 全局展示编码时长统计
  - 安全的API密钥管理
- QAnything AI问答服务
  - 自主开发的问答界面
  - API接口集成
  - 实时响应处理
  - 主题分类
  - 历史记录

## 技术栈

- Next.js 14
- React
- TypeScript
- Tailwind CSS
- WakaTime API
- QAnything API

## QAnything集成路径说明

本项目选择了路径二（API自行开发），原因如下：

1. 更好的用户体验
   - 自定义UI设计
   - 实时响应反馈
   - 主题分类功能
   - 历史记录保存

2. 安全性考虑
   - API密钥通过环境变量管理
   - 使用API路由保护密钥
   - 请求验证和错误处理

3. 开发经验提升
   - 深入理解API集成
   - 前端状态管理
   - 用户界面设计
   - 错误处理最佳实践

### 实现细节

1. API路由实现
   - 创建`/api/qa`路由处理请求
   - 环境变量配置
   - 错误处理和状态码

2. 前端功能
   - 主题分类
   - 实时响应
   - 历史记录
   - 加载状态
   - 错误提示

## WakaTime API集成

1. 安全配置
   - 环境变量管理API密钥
   - 服务端请求

2. 数据展示
   - 全局页脚展示
   - 自动更新
   - 格式化显示

## 项目结构

```
src/
  ├── app/                 # App Router 路由
  │   ├── api/            # API路由
  │   ├── exercises/      # 课程练习路由
  │   ├── qa/            # QAnything问答界面
  │   └── page.tsx       # 首页
  ├── components/         # React组件
  │   ├── layout/        # 布局组件
  │   ├── exercises/     # 练习相关组件
  │   └── qa/           # 问答相关组件
  ├── lib/               # 工具函数和配置
  │   ├── wakatime.ts   # WakaTime API封装
  │   └── qanything.ts  # QAnything API封装
  └── types/             # TypeScript类型定义
```

## 环境变量配置

创建`.env.local`文件并配置以下环境变量：

```bash
# WakaTime API配置
WAKATIME_API_KEY=your_wakatime_api_key

# QAnything API配置
QANYTHING_API_ENDPOINT=your_qanything_api_endpoint
QANYTHING_API_KEY=your_qanything_api_key
```

## 运行说明

1. 安装依赖：
```bash
npm install
```

2. 配置环境变量：
   - 复制`.env.example`到`.env.local`
   - 填入相应的API密钥

3. 开发环境运行：
```bash
npm run dev
```

4. 生产环境构建：
```bash
npm run build
npm start
```

## 运行截图

### QAnything问答界面
[截图待添加]

### WakaTime统计展示
[截图待添加]

### 课程练习导航
[截图待添加]

## 代码规范

- 使用ESLint和Prettier保持代码风格一致
- 遵循TypeScript类型安全
- 组件和函数使用清晰的命名
- 添加必要的注释说明
- 使用Git进行版本控制

## 项目特点

1. 高级特性应用
   - Next.js App Router
   - API Routes
   - 环境变量管理
   - TypeScript类型安全

2. 用户体验优化
   - 响应式设计
   - 加载状态
   - 错误处理
   - 主题分类

3. 安全性考虑
   - API密钥保护
   - 请求验证
   - 错误处理

4. 可维护性
   - 清晰的项目结构
   - 类型定义
   - 组件化开发
   - 文档完善
