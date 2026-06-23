# Agent_Study

这是我的 Agent 学习项目，用来从零拆解一个 coding agent 的核心机制。

项目按章节推进，每个 `sXX_*` 目录对应一个独立主题。每章尽量保持一个核心 `code.py`，方便直接运行、对比和实验。

## 学习目标

- 理解 agent loop 的基本结构
- 学习模型如何发起 tool use
- 学习工具执行、权限检查、hook 等机制
- 用尽量少的代码复现 coding agent 的关键组成
- 保持每个章节都能独立运行和调试

## 当前章节

```text
Agent_Study/
├─ s01_agent_loop/     # 最小 agent loop：模型调用工具直到停止
├─ s02_tool_use/       # 工具分发：从一个 bash 工具扩展到多个工具
├─ s03_permission/     # 权限控制：执行工具前判断是否允许
├─ s04_hooks/          # Hooks：在工具执行前后插入可扩展逻辑
├─ requirements.txt    # Python 依赖
└─ README.md
```

后续会继续补充 `s05` 到 `s20`，每章只聚焦一个 agent 机制。

## 运行环境

建议使用 Python 3.10+。

安装依赖：

```powershell
python -m pip install -r requirements.txt
```

## 环境变量

本地创建 `.env` 文件保存 API Key。`.env` 不会提交到 GitHub。

示例：

```text
ANTHROPIC_API_KEY=your_api_key
MODEL_ID=claude-opus-4-7
```

如果使用兼容 Anthropic API 的模型服务，可以配置：

```text
ANTHROPIC_API_KEY=your_api_key
ANTHROPIC_BASE_URL=https://example.com/anthropic
MODEL_ID=your_model_id
```

## 运行章节

进入项目根目录后运行：

```powershell
python .\s01_agent_loop\code.py
```

也可以进入某个章节目录运行：

```powershell
cd .\s01_agent_loop
python code.py
```

每个章节都是交互式程序，输入问题后观察模型如何调用工具、追加消息并继续循环。

## 项目原则

- 代码优先服务学习，不追求完整生产框架。
- 每章只引入一个主要概念，避免一次加入太多抽象。
- 能单文件表达的逻辑就先保持单文件。
- API Key、缓存文件和本地环境文件不进入仓库。
- 涉及文件或命令执行时，优先考虑安全边界。

## 备注

这是一个学习仓库，不是生产可用的 agent 框架。代码会随着学习进度持续调整，重点是理解机制，而不是封装成稳定库。
