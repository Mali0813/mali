# QAnything API 配置指南

## 概述

本项目已集成 QAnything 大语言模型问答服务，提供智能的高考志愿填报咨询服务。

## 配置步骤

### 1. 注册 QAnything 账户

1. 访问 [QAnything 平台](https://ai.youdao.com/qanything/docs/intro/api-intro)
2. 注册并登录您的账户

### 2. 获取 API 密钥

#### 管理秘钥（用于知识库管理）
1. 登录后进入"个人账号-API 秘钥"
2. 创建或复制您的管理秘钥

#### 问答秘钥（用于 Agent 问答）
1. 进入"Agents-发布-API 秘钥"
2. 创建或复制您的问答秘钥

### 3. 创建或选择 Agent

1. 在 QAnything 平台创建新的 Agent
2. 或者选择现有的 Agent
3. 记录 Agent ID

### 4. 配置环境变量

在项目根目录创建 `.env.local` 文件，添加以下配置：

```env
# QAnything API 配置
QANYTHING_API_KEY=your_qa_api_key_here
QANYTHING_AGENT_ID=your_agent_id_here

# WakaTime API 配置（可选）
WAKATIME_API_KEY=your_wakatime_api_key_here
```

**重要说明：**
- `QANYTHING_API_KEY` 应使用**问答秘钥**，不是管理秘钥
- `QANYTHING_AGENT_ID` 是您创建的 Agent 的 ID

### 5. 重启开发服务器

```bash
npm run dev
```

## API 接口说明

### 使用的接口
- **接口地址**: `https://openapi.youdao.com/q_anything/api/chat`
- **接口类型**: Agent 问答 (stream)
- **请求方法**: POST
- **认证方式**: Authorization Header

### 请求参数
```json
{
  "agentId": "your_agent_id",
  "question": "用户问题",
  "stream": false,
  "history": []
}
```

### 响应格式
```json
{
  "errorCode": 0,
  "msg": "SUCCESS",
  "result": {
    "answer": "AI 回答内容"
  }
}
```

## 故障排除

### 1. API Key 未配置
**症状**: 控制台显示"QAnything API Key 未配置"
**解决**: 检查 `.env.local` 文件中的 `QANYTHING_API_KEY` 配置

### 2. Agent ID 未配置
**症状**: 控制台显示"QAnything Agent ID 未配置"
**解决**: 检查 `.env.local` 文件中的 `QANYTHING_AGENT_ID` 配置

### 3. API 调用失败
**症状**: 问答功能返回备用回复
**可能原因**:
- API Key 无效或过期
- Agent ID 不正确
- 网络连接问题
- QAnything 服务暂时不可用

**解决步骤**:
1. 验证 API Key 和 Agent ID 的正确性
2. 检查网络连接
3. 查看浏览器控制台的错误信息
4. 稍后重试

### 4. 权限问题
**症状**: API 返回权限错误
**解决**: 确保使用的是问答秘钥，而不是管理秘钥

## 备用机制

当 QAnything API 调用失败时，系统会自动使用本地备用回复，确保问答功能始终可用。备用回复涵盖以下关键词：

- 高考
- 志愿
- 专业
- 分数
- 学校
- 填报
- 批次
- 复读
- 调剂

## 扩展功能

### 历史对话记录
当前实现使用空的 `history` 数组。如需支持多轮对话，可以扩展实现：

1. 在前端保存对话历史
2. 将历史对话传递给 API
3. 实现上下文感知的问答

### 流式响应
当前使用非流式响应 (`stream: false`)。如需实现打字机效果，可以：

1. 设置 `stream: true`
2. 处理流式响应数据
3. 实现实时显示效果

## 相关链接

- [QAnything API 文档](https://ai.youdao.com/qanything/docs/intro/api-intro)
- [知识库管理 API](https://ai.youdao.com/qanything/docs/api/dataset)
- [Agent 管理 API](https://ai.youdao.com/qanything/docs/api/agent)
- [流式问答 API](https://ai.youdao.com/qanything/docs/api/chat)
- [错误码说明](https://ai.youdao.com/qanything/docs/api/errorCode) 