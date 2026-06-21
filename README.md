# LLM 工程文档站

面向**资深程序员**的 Claude 与 OpenAI API / Agent 实战讲解 —— 逐行代码、最佳实践、踩坑提示,以及两家的横向对照。所有内容对照官方 SDK 与文档的**真实行为**,不是凭印象。

> 🌐 **在线阅读**:<https://zhangrongyu20260218-oss.github.io/UknowClaude/>

---

## 📚 文档

| 文档 | 在线 | 一句话 |
|---|---|---|
| **用 Agent SDK 造一个真实应用** | [打开](https://zhangrongyu20260218-oss.github.io/UknowClaude/claude-agent-sdk-app-tutorial.html) · [`claude-agent-sdk-app-tutorial.html`](./claude-agent-sdk-app-tutorial.html) | 从零造一个能跑的 CLI 编码 Agent(`miniclaude`),逐行讲解 Agent 全部核心能力 |
| **Claude Managed Agents 完整讲解** | [打开](https://zhangrongyu20260218-oss.github.io/UknowClaude/claude-managed-agents-guide.html) · [`claude-managed-agents-guide.html`](./claude-managed-agents-guide.html) | Agent / Environment / Session / Events 托管运行时完整讲解 + OpenAI Agents SDK 对照 |
| **Claude Opus Message API 完整讲解** | [打开](https://zhangrongyu20260218-oss.github.io/UknowClaude/opus-message-api-guide.html) · [`opus-message-api-guide.html`](./opus-message-api-guide.html) | 把 Message API 当成「带几处反直觉行为的 HTTP 端点」吃透 |
| **OpenAI 三套 API 完整讲解** | [打开](https://zhangrongyu20260218-oss.github.io/UknowClaude/openai-apis-tutorial.html) · [`openai-apis-tutorial.html`](./openai-apis-tutorial.html) | Chat Completions / Responses / Agents SDK 逐行讲解 + 与 Anthropic 对照 |

默认模型:Claude 侧 `claude-opus-4-8`,OpenAI 侧示例用官方当前示例模型(请按可用模型替换)。

---

## 🧭 各文档覆盖什么

### 用 Agent SDK 造一个真实应用(Anthropic)
- Agent 心智模型(model + tools 的循环)、何时**不**该造 Agent
- 工具面设计与安全边界(bash vs 专用工具)、带路径/命令校验的执行器
- **手写 agentic loop** 逐行(含三大高频 bug)、Tool Runner 对照
- **流式事件全解**(7.1–7.8):所有 SSE 事件与 delta 类型、`input_json_delta`/`partial_json` 累积、thinking + `signature_delta`
- 服务端工具与 `pause_turn`
- **Prompt Caching 深水区**(9):TTL/最小长度、失效层级、20-block 回溯、**会话内 `role:"system"` 消息**、预热与 `count_tokens`
- Compaction / Context Editing、跨会话 memory、结构化输出 / 子代理
- 错误处理 / refusal / 人审、完整 `main.py`

### Claude Managed Agents 完整讲解(Anthropic)
- 托管边界与选型:Messages API / Claude Agent SDK / Managed Agents 三层关系
- **四资源模型**:版本化 Agent、Environment、安全沙箱、Session 状态机、追加式 Events
- 可运行 Python 主线、SSE 消费、断线补历史、`idle` / `requires_action` 正确处理
- 内置工具、MCP、Custom Tools、permission policy、人审与宿主鉴权
- Files / GitHub / Skills / Vault、Outcomes 自评迭代、Multiagent persistent threads
- Webhook、Scheduled Deployments、生产控制面、成本/限制/ZDR 边界
- **Claude Managed Agents ↔ OpenAI Agents SDK 横向对照**

### Claude Opus Message API 完整讲解(Anthropic)
- 认证与传输层、请求结构、多模态、Thinking / Effort、stop_reason
- 流式、Tool Use、服务端/客户端工具、上下文与成本优化、结构化输出
- 错误处理、多轮会话、长跑 coding agent 整合

### OpenAI 三套 API 完整讲解
- 三套 API 的**分层关系**与选型
- **Chat Completions**:roles、流式增量 arguments、函数调用循环、结构化输出
- **Responses**:`input`/`output` items、`previous_response_id` 有状态、内置工具、扁平 function tool、`reasoning.effort`、语义化 `response.*` 流式事件
- **Agents SDK**:Agent + Runner、`@function_tool`、handoffs、guardrails、sessions、流式事件、tracing
- **三套写法对照**(同一个 agent 写三遍)、**错误处理与重试**
- **RAG**:Embeddings 自管 / Vector Store + `file_search` 托管、自动缓存、Batch
- **OpenAI ↔ Anthropic 横向对照表**(迁移用)

---

## 👀 怎么看

- **在线(推荐)**:点上面的链接,GitHub Pages 已部署。
- **本地**:每份都是**自包含单文件 HTML**(内联 CSS/JS,无外部依赖),下载后双击即可在浏览器打开。
- 直接在 GitHub 仓库里点 `.html` 只会显示源码(GitHub 不渲染 HTML),用上面两种方式。

---

## 🚀 部署

GitHub Pages 已开启:**Settings → Pages → Source = Deploy from a branch → `main` / (root)**。
向 `main` 推任何改动后,Pages 自动重建,几分钟后生效。根目录的 `index.html` 是目录首页。

---

## ✅ 准确性

- 全文对照 Anthropic / OpenAI 官方 SDK 与文档的真实行为;关键的流式事件、字段名、API 标识均逐项核对。
- Claude Managed Agents 目前仍为 beta;对应文档标注了核对日期与 `managed-agents-2026-04-01` beta 版本。
- OpenAI 的模型字符串、内置工具 `type`、`.parse` 命名空间等**易变项**已在文中标注「以你写代码当天的官方文档为准」。

## 📄 许可

文档内容供学习参考。
