<p align="center">
    <a href="https://linux.do/t/topic/2108966/20" alt="LINUX DO">
        <img
            src="https://img.shields.io/badge/LINUX-DO-FFB003.svg?logo=data:image/svg%2bxml;base64,DQo8c3ZnIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZyIgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxMDAiPjxwYXRoIGQ9Ik02OC4yLS4wNTVoNi4yNXEyMy45NjkgMi4wNjIgMzggMjEuNDI2YzUuMjU4IDcuNjc2IDguMjE1IDE2LjE1NiA4Ljg3NSAyNS40NXY2LjI1cS0yLjA2NC0yMy45NjgtMjEuNDMgMzgtMTEuNTEyIDcuODg1LTI1LjQ0NSA4Ljg3NGgtNi4yNXEtMjMuOTctMi4wNjQtMzguMDA0LTIxLjQzUVUuOTcxIDY3LjA1Ni0uMDU0IDUzLjE4di02LjQ3M0MxLjM2MiAzMC43ODEgOC41MDMgMTguMTQ4IDIxLjM3IDguODE3IDI5LjA0NyAzLjU2MiAzNy41MjcuNjA0IDQ2LjgyMS0uMDU2IiBzdHlsZT0ic3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOmV2ZW5vZGQ7ZmlsbDojZWNlY2VjO2ZpbGwtb3BhY2l0eToxIi8+PHBhdGggZD0iTTQ3LjI2NiAyLjk1N3EyMi41My0uNjUgMzcuNzc3IDE1LjczOGE0OS43IDQ5LjcgMCAwIDEgNi44NjcgMTAuMTU3cS00MS45NjQuMjIyLTgzLjkzIDAgOS43NS0xOC42MTYgMzAuMDI0LTI0LjM4N2E2MSA2MSAwIDAgMSA5LjI2Mi0xLjUwOCIgc3R5bGU9InN0cm9rZTpub25lO2ZpbGwtcnVsZTpldmVub2RkO2ZpbGw6IzE5MTkxOTtmaWxsLW9wYWNpdHk6MSIvPjxwYXRoIGQ9Ik03Ljk4IDcwLjkyNmMyNy45NzctLjAzNSA1NS45NTQgMCA4My45My4xMTNRODMuNDI2IDg3LjQ3MyA2Ni4xMyA5NC4wODZxLTE4LjgxIDYuNTQ0LTM2LjgzMi0xLjg5OC0xNC4yMDMtNy4wOS0yMS4zMTctMjEuMjYyIiBzdHlsZT0ic3Ryb2tlOm5vbmU7ZmlsbC1ydWxlOmV2ZW5vZGQ7ZmlsbDojZjlhZjAwO2ZpbGwtb3BhY2l0eToxIi8+PC9zdmc+" /></a>
    <a href="https://dev.to/_879c5a0279451d52e43c3/aegis-a-method-pack-for-more-reliable-ai-coding-agents-1gfm" alt="DEV.to">
        <img src="https://img.shields.io/badge/DEV.to-Article-0A0A0A?logo=devdotto&logoColor=white" /></a>
    <a href="https://github.com/GanyuanRan/Aegis/actions/workflows/ci.yml" alt="CI">
        <img src="https://img.shields.io/github/actions/workflow/status/GanyuanRan/Aegis/ci.yml?branch=main&label=CI" /></a>
    <a href="https://github.com/GanyuanRan/Aegis/releases/latest" alt="最新发布">
        <img src="https://badgen.net/github/release/GanyuanRan/Aegis?label=Latest%20Release" /></a>
</p>

<p align="center">
    <img src="assets/aegis-hero.png" alt="Aegis 架构驱动 AI 编程 agent 头图" />
</p>

# Aegis

<p align="center">
    <strong>Aegis Method Pack</strong><br/>
    面向 AI 编程 agent 的 baseline-first、evidence-driven 工作流程纪律包。
</p>

<p align="center">
    <a href="README.md"><strong>中文主页</strong></a>
    ·
    <a href="README.en.md"><strong>兼容入口（中文）</strong></a>
    ·
    <a href="docs/current/AEGIS_WORKFLOW_GUIDE_ZH.md">工作流程说明</a>
</p>

> 说明：此文件名保留为 `README.en.md`，用于兼容历史链接和测试路径；项目默认文档语言已统一为中文。命令名、文件名、宿主名和协议字段保持原文，避免破坏安装与运行。

## 为什么需要 Aegis

Aegis 是面向真实软件工作的 **Superpowers 升级版**。它保留可组合 skill 的优点，并进一步加入：

- **Baseline first**：高风险改动前先读取当前项目事实和权威说明。
- **Evidence before claims**：没有新的验证证据，就不声明完成。
- **Repair plus retirement**：修复问题时同步说明旧路径保留、迁移或退役。
- **Workflow Quality**：简单任务保持轻量，风险升高才展开更完整流程。
- **多宿主 method-pack**：同一套方法可安装到多个支持 skill 的宿主。

当 agent 容易在目标、owner、架构边界或验证路径尚未明确时就开始写代码，Aegis 会把工作拉回更稳的工程节奏。

## 极简安装

把下面这段话交给你的 AI 编程 Agent：

```text
请阅读 https://github.com/GanyuanRan/Aegis，识别我当前使用的 AI 编程宿主，并按对应宿主说明全局安装 Aegis。如果需要重启或重新加载宿主，请明确告诉我；然后从已安装的 Aegis method-pack 根目录运行完整安装验证。不要在目标项目目录中运行 doctor 命令。先定位 `<aegis-method-pack-root>`，再运行 `cd <aegis-method-pack-root> && python scripts/aegis-doctor.py --write-config --json`。只有当 JSON 输出包含 `"ok": true`、`"workspaceSupport": "available"` 和 `"configStatus": "configured"` 时，才把安装视为完成；如果宿主有单独的 skill discovery 目录，也要额外用 `--discovery-root <path>` 验证它指向当前版本。
```

## 更新 Aegis

完成安装并登记当前宿主后，后续更新可以自然描述为 `更新 Aegis`，也可以显式说 `aegis:update`。agent 应定位本机已安装的 method-pack 根目录，读取 host-scoped registry，并默认只更新当前宿主。只有用户明确要求 `--all` 时才更新所有已登记宿主。Aegis 默认不做后台自动更新。

## 使用前必须知道

Aegis 当前发布形态是：

> `Aegis Method Pack (runtime-ready)`

它不是完整的 Aegis Platform，不是 daemon，不是后台 runner，不是 runtime core，不提供 authoritative `GateDecision`，不提供 authoritative `PolicySnapshot`，也不授予 final completion authority。用户当前指令和目标项目规则始终优先于 Aegis。

为了让宿主级行为更顺滑，可以使用：

- [轻量全局规则](GLOBAL_USER_RULES_LITE.zh-CN.md)
- [高级全局规则模板](GLOBAL_USER_RULES_TEMPLATE.zh-CN.md)

Aegis 默认是自动模式。要切换到显式模式，请在已安装的 method-pack 根目录运行：

```bash
cd <aegis-method-pack-root>
python scripts/aegis-doctor.py activation-mode explicit
```

修改后需要重启宿主。长期设置方式和宿主注意事项见 [activation mode 文档](docs/current/AEGIS_ACTIVATION_MODE.md)。

TDD mode 默认是 `auto`：Aegis 会按风险自动选择严格 TDD、轻量验证，或在不适合 TDD 的任务中跳过 TDD。若只想关闭自动 TDD 路由，但仍保留完成前验证：

```bash
cd <aegis-method-pack-root>
python scripts/aegis-doctor.py tdd-mode off
```

详细语义见 [TDD mode 文档](docs/current/AEGIS_TDD_MODE.md)。

## 宿主兼容性

Aegis 保留多宿主、plugin-installable 的分发目标。

| 宿主组 | 当前状态 | 从这里开始 |
| --- | --- | --- |
| `Codex`, `OpenCode` | 当前 method-pack 范围内已有 fresh evidence | [Codex](docs/README.codex.md), [OpenCode](docs/README.opencode.md) |
| `Claude Code`, `CodeBuddy`, `DeepSeek-TUI`, `Trae`, `GitHub Copilot`, `Qoder` | 已有安装说明；release-level fresh host smoke 仍待补证 | [Claude Code](docs/README.claude-code.md), [CodeBuddy](docs/README.codebuddy.md), [DeepSeek-TUI](docs/README.deepseek-tui.md), [Trae](docs/README.trae.md), [GitHub Copilot](docs/README.copilot.md), [Qoder](docs/README.qoder.md) |
| `CC GUI (JetBrains IDEA)` | Claude Code / OpenAI-GPT 通道的 IDE 插件层结构性支持；release-level fresh host smoke 仍待补证 | [CC GUI](docs/README.cc-gui.md) |
| `Antigravity CLI`, `Antigravity IDE`, `Antigravity App` | 结构性目标；release-level fresh host smoke 仍待补证 | [Antigravity](docs/README.antigravity.md) |
| `Pi CLI`, `OpenClaw`, `Hermes Agent` | 结构性 Agent Skills / `SKILL.md` skill-host 适配；release-level fresh host smoke 仍待补证 | [Pi CLI](docs/README.pi.md), [OpenClaw](docs/README.openclaw.md), [Hermes Agent](docs/README.hermes-agent.md) |
| `Gemini CLI` | Antigravity 支持成熟前的过渡兼容面 | [兼容性矩阵](docs/current/AEGIS_HOST_COMPATIBILITY_MATRIX_SNAPSHOT.md) |

对外声明支持状态前，请先阅读：

- [宿主兼容性矩阵](docs/current/AEGIS_HOST_COMPATIBILITY_MATRIX_SNAPSHOT.md)
- [已知限制](docs/current/AEGIS_KNOWN_LIMITATIONS.md)

## 如何使用

安装并重启宿主后，直接自然描述开发任务即可。任务匹配时，agent 应选择对应 Aegis 方法。

高风险任务前可以先用轻量目标框定；它会先框定目标，然后默认继续进入已选 workflow：

```text
Aegis goal: 修复登录后偶发跳回登录页，不重写 auth 系统。
```

当你想强制指定方法时，可以显式点名 skill：

- `aegis:brainstorming`
- `aegis:systematic-debugging`
- `aegis:writing-plans`
- `aegis:first-principles-review`
- `aegis:requesting-code-review`
- `aegis:verification-before-completion`

如果预期 skill 没有触发，不要先当成提示词措辞问题。应按触发链路诊断：安装/版本可见性、宿主 skill discovery、activation mode、`using-aegis` 路由、任务到 skill 的匹配，以及上下文压力。详见 [触发健康基线](docs/current/AEGIS_TRIGGER_HEALTH_BASELINE.md)。

## 工作流形态

Aegis 在实施前按复杂度路由：

- 低复杂度：简短 intent、baseline check、TDD Route、验证。
- 中复杂度：baseline read set、Spec Brief 或稳定需求、writing plan、atomic tasks、验证。
- 高复杂度：Design Spec、plan、必要时用户确认，然后执行。

核心纪律是：

- **Baseline first**：重大改动前先读当前项目 authority。
- **Evidence before claims**：没有 fresh verification evidence，不声明完成。
- **Repair plus retirement**：修复 owner，同时说明旧路径保留或退役。
- **Workflow Quality**：简单任务保持轻量，风险升高才展开。

完整说明见：

- [工作流程说明](docs/current/AEGIS_WORKFLOW_GUIDE_ZH.md)
- [工作流质量基线](docs/current/AEGIS_WORKFLOW_QUALITY_BASELINE.md)
- [Runtime-ready 边界](docs/current/AEGIS_RUNTIME_READY_BOUNDARY.md)
- [Artifact schema baseline](docs/current/AEGIS_ARTIFACT_SCHEMA_BASELINE.md)

## 维护者入口

主要验证入口：

```bash
bash tests/e2e/run-all.sh --full --host-profile fast
```

聚焦文档 / method-pack 检查：

```bash
bash tests/e2e/boundary-compliance-check.sh
bash tests/e2e/workflow-quality-check.sh
bash tests/e2e/install-verification-policy-check.sh
bash tests/e2e/layer1-fast-check.sh --host-profile none
```

建议阅读：

- [测试说明](docs/testing.md)
- [发布检查清单](docs/current/AEGIS_METHOD_PACK_RELEASE_CHECKLIST.md)
- [当前 authority map](docs/current/README.md)
- [贡献指南](CONTRIBUTING.md)

## 与 Superpowers 的关系

Aegis 派生自 **[Superpowers](https://github.com/obra/superpowers)**，由 [Jesse Vincent](https://github.com/obra) 创建。Superpowers 开创了可组合、多 harness agent skills 的形态。Aegis 保留这个基础，并为真实软件项目加入架构与证据驱动的方法层。

其他灵感来自 [mattpocock/skills](https://github.com/mattpocock/skills)，尤其是简洁沟通、共享语言和纪律化调试模式。这些想法以 Aegis 格式重新实现，而不是逐字复制。

## 许可证

MIT License。详见 [LICENSE](LICENSE)。
