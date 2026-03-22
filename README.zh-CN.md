<!-- language-switch:start -->
[English](./README.md) | [中文](./README.zh-CN.md)
<!-- language-switch:end -->

<p align="center">
<img src="docs/images/banner.svg" alt="freeact" width="100%">
</p>

<p align="left">
<a href="https://gradion-ai.github.io/freeact/"><img alt="网站" src="https://img.shields.io/website?url=https%3A%2F%2Fgradion-ai.github.io%2Ffreeact%2F&up_message=online&down_message=offline&label=docs"></a>
<a href="https://pypi.org/project/freeact/"><img alt="PyPI - 版本" src="https://img.shields.io/pypi/v/freeact?color=blue"></a>
<a href="https://github.com/gradion-ai/freeact/releases"><img alt="GitHub 发布" src="https://img.shields.io/github/v/release/gradion-ai/freeact"></a>
<a href="https://github.com/gradion-ai/freeact/actions"><img alt="GitHub 操作工作流程状态" src="https://img.shields.io/github/actions/workflow/status/gradion-ai/freeact/test.yml"></a>
<a href="https://github.com/gradion-ai/freeact/blob/main/LICENSE"><img alt="GitHub 许可证" src="https://img.shields.io/github/license/gradion-ai/freeact?color=blueviolet"></a>
</p>

Freeact 是一个轻量级代理工具和 CLI 工具，通过执行 Python 代码和 shell 命令来起作用。代码操作是代理改进自身及其工具库的关键。

它为 MCP 服务器生成 Python API，并以编程方式（“代码模式”）而不是 JSON 调用其工具。这使得在单个推理过程中可以在代码操作中组合工具。

Freeact 有一个微小的核心，并使用沙盒 IPython 内核以统一的方式执行 Python 代码和 shell 命令。执行在本地运行，并对操作进行细粒度的批准。

> [！笔记]
> **支持的型号**：Freeact 支持与 [Pydantic AI](https://ai.pydantic.dev/) 兼容的任何型号，默认为 `gemini-3-flash-preview`。有关提供程序配置和示例，请参阅[型号](https://gradion-ai.github.io/freeact/models/)。

## 文档

- 📚 [文档](https://gradion-ai.github.io/freeact/)
- 🚀 [快速入门](https://gradion-ai.github.io/freeact/quickstart/)
- 🤖 [llms.txt](https://gradion-ai.github.io/freeact/llms.txt)
- 🤖 [llms-full.txt](https://gradion-ai.github.io/freeact/llms-full.txt)

## 能力

|能力|描述 |
|---|---|
| **代码操作** | Freeact 代理通过 Python 代码和 shell 命令进行操作。这使得在单个 LLM 推理过程中实现工具组合和中间结果处理。 |
| **本地执行** | Freeact 在 [ipybox](https://github.com/gradion-ai/ipybox) 提供的 IPython 内核中本地执行代码和 shell 命令。数据、配置和生成的工具位于本地工作区中。 |
| **沙盒模式** | IPython 内核可以选择在基于 Anthropic 的 [sandbox-runtime](https://github.com/anthropic-experimental/sandbox-runtime) 的沙箱环境中运行。它在操作系统级别强制执行文件系统和网络限制。 |
| **MCP 代码模式** | Freeact 通过生成的 Python API 以编程方式调用 MCP 服务器工具<sup>1)</sup>。这使得在代码操作中组合工具调用的延迟要低得多。 |
| **工具发现** |通过类别浏览或混合 BM25/矢量搜索来发现工具。按需加载可以释放上下文窗口并扩展到更大的工具库。 |
| **工具创作** |代理可以创建新工具、增强现有工具或将代码操作保存为可重用工具。这将成功的经验捕获为可执行的知识。 |
| **代理技巧** |技能为代理提供基于 [agentskills.io](https://agentskills.io/) 的新能力和专业知识。它们自然地与代码操作和代理编写的工具组合。 |
| **子代理授权** |任务可以委托给子代理，每个子代理使用自己的沙箱。它可以实现专业化和并行化，而不会扰乱主智能体的上下文。 |
| **行动批准** |对来自主代理和子智能体的代码操作和（编程）工具调用进行细粒度批准。使人类能够控制潜在的危险行为。 |
| **会话持续性** | Freeact 增量地保留代理状态。持久会话可以恢复并作为调试、评估和改进的记录。 |

## 用法

|组件|描述 |
|---|---|
| **[代理SDK](https://gradion-ai.github.io/freeact/sdk/)** |用于构建 freeact 应用程序的代理工具和 Python API。 |
| **[CLI 工具](https://gradion-ai.github.io/freeact/cli/)** |用于与 freeact 代理进行交互式对话的终端界面。 |

---

<sup>1)</sup> Freeact 还支持通过 JSON 工具调用进行 MCP 服务器集成，但推荐的方法是编程工具调用。
