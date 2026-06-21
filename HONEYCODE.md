# HoneyCode 项目

## 技术栈

- Python 3.11+ / Textual（终端 TUI）
- Anthropic / OpenAI SDK（多提供商接入，含 prompt caching）
- MCP 协议（Model Context Protocol）
- Pydantic（数据模型与参数校验）
- uv（依赖管理与虚拟环境）

## 代码规范

- commit message 用英文
- 变量命名用 snake_case
- 模块与函数命名用 snake_case，类名用 PascalCase
- 公开模块、类、函数均写中文 docstring，说明职责与关键设计取舍
- 工具（Tool）统一继承 `honeycode.tools.base.Tool`，
  实现 `name` / `description` / `parameters` / `execute`，由 `ToolRegistry` 统一注册与调度
- 新增工具时同步更新 `honeycode/tools/__init__.py` 的导出列表
- 新增 Slash 命令时在 `honeycode/commands/handlers/` 下实现并注册到命令表
- 不在代码中写入密钥，统一走环境变量或 YAML 配置
