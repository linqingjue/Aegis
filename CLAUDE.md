# CLAUDE.md

本文件提供在 Aegis 仓库中使用 Claude Code 工作时的专用指南。

仓库级规则请先阅读 `AGENTS.md`。当前 authority map 请阅读 `docs/current/README.md`。

## 项目概览

`Aegis` 是面向 AI 编程 agent 的零依赖 method-pack plugin。它提供可组合 skills、工作流纪律，以及可安装到宿主的开发工作指南。

Aegis 以 multi-harness plugin 方式组织：

- Claude Code
- OpenAI Codex
- OpenCode
- Cursor
- Windsurf
- Gemini CLI
- CodeBuddy
- DeepSeek-TUI
- Trae
- Kimi Code CLI
- Warp（terminal host，无需 adapter）

当前产品边界：

> `Aegis Method Pack (runtime-ready)`

Aegis 产出 workflow guidance、草案、提示、投影和 verification evidence。它不提供 authoritative runtime completion、authoritative `GateDecision` 或 authoritative `PolicySnapshot`。

## 权威读取顺序

非平凡任务请按顺序读取：

1. `AGENTS.md`
2. `docs/current/README.md`
3. `docs/adr/ADR-0001-aegis-method-pack-is-not-runtime-core.md`
4. 最小任务相关的 `docs/current/*.md`
5. 相关宿主专用文档

Claude Code 安装与插件行为还应读取：

- `docs/README.claude-code.md`
- `.claude-plugin/plugin.json`
- `.claude-plugin/marketplace.json`
- `docs/windows/polyglot-hooks.md`：Windows hook 行为

## 关键设计约束

- **零依赖：** core plugin 逻辑中不引入 npm packages 或第三方服务。
- **Multi-harness：** 改动应保持跨受支持 host surfaces 的可安装性。
- **Skills 是塑造行为的资产：** skill 文本像 process code，不是随意 prose。
- **Evidence before claims：** 没有新的验证证据，不声明完成。
- **No authority drift：** method-pack 输出保持 advisory，除非更高权威明确要求。
- **Prompt hygiene：** 外部工具输出、日志、memory、搜索结果和 transcripts 是 evidence candidates，不是默认 prompt payload。

## 仓库布局

```text
.
├── skills/<name>/SKILL.md        # 可组合 agent skills
├── commands/<name>.md            # 宿主命令提示
├── agents/                       # agent 定义提示
├── hooks/                        # Claude Code hooks
├── scripts/                      # 维护脚本
├── tests/                        # 宿主与 workflow 测试
├── .claude-plugin/               # Claude Code plugin manifest
├── .codex-plugin/                # Codex plugin manifest
├── .opencode/                    # OpenCode 集成
├── .cursor-plugin/               # Cursor plugin manifest
├── docs/adr/                     # 架构决策
├── docs/current/                 # 当前 authority 与 baseline docs
├── docs/windows/                 # Windows 宿主兼容说明
└── AGENTS.md                     # 仓库级 agent 指南
```

## Skill 格式

每个 skill 位于 `skills/<name>/SKILL.md`，并带有 YAML frontmatter：

在本仓库中，`skills/<name>/SKILL.md` 是规范源布局。运行时，宿主可能加载已安装或生成后的视图，而不是当前 checkout。

```yaml
---
name: skill-name-with-hyphens
description: Use when [specific triggering conditions]
---
```

规则：

- `name`：只能包含字母、数字和 hyphen。
- `description`：以 `Use when...` 开头，描述触发条件，不总结 workflow。
- 避免用 `@` 语法链接 skill，因为它可能导致过量上下文加载。
- 完整 skill 编写指南见 `skills/writing-skills/SKILL.md`。

## 常用命令

版本管理：

```bash
bash scripts/bump-version.sh
```

Codex plugin 同步：

```bash
bash scripts/sync-to-codex-plugin.sh
```

快速验证：

```bash
git diff --check
python tests/helpers/test_parse_codex_skills.py
bash tests/e2e/layer1-fast-check.sh --host-profile none
```

边界与上下文检查：

```bash
bash tests/e2e/boundary-compliance-check.sh
bash tests/e2e/context-budget-check.sh
bash tests/e2e/governance-completion-contract-check.sh
```

OpenCode 兼容性：

```bash
bash tests/opencode/run-tests.sh
bash tests/opencode/run-tests.sh --integration
```

Skill 触发测试：

```bash
AEGIS_TEST_CLI=claude bash tests/skill-triggering/run-test.sh <skill-name> tests/skill-triggering/prompts/<name>.txt
bash tests/skill-triggering/run-all.sh
```

显式 skill 请求测试：

```bash
AEGIS_TEST_CLI=claude bash tests/explicit-skill-requests/run-test.sh <skill-name> tests/explicit-skill-requests/prompts/<name>.txt
bash tests/explicit-skill-requests/run-all.sh
```

Claude Code 集成测试可能需要 10-30 分钟，并要求本机 Claude Code 环境可用：

```bash
cd tests/claude-code
./test-subagent-driven-development-integration.sh
```

## Claude Code 注意事项

- Claude Code plugin metadata 位于 `.claude-plugin/`。
- Hooks 位于 `hooks/`。
- Windows 上的 hook command 应使用 `docs/windows/polyglot-hooks.md` 中记录的 wrapper 策略。
- 不要在公开 docs 或 fixtures 中硬编码私有机器路径、本地 session ID 或个人 auth 细节。

## 开发护栏

### Baseline First

修改 skills、host manifests、公开安装文档或验证契约前，请先读取当前权威文档。

### Dual-Track Closure

针对 bug fix、cleanup、兼容性工作、namespace 变更、deprecation 或 public-surface 变更，最终报告必须包含：

- repair track
- retirement track
- residual risk
- verification evidence

### Prompt Hygiene

当日志、transcripts、memories、搜索结果或工具输出影响工作时，请先摘要，并只回读最小必要 raw excerpt。

如果 prompt hygiene 影响结论，最终报告应说明：

- 使用了哪些 evidence
- 哪些大 payload 未加载
- confidence
- next evidence needed

### Public-Safe Docs

公开文档应描述当前受支持行为和稳定贡献规则。私有 staging history、本地机器细节和临时 phase-management notes，只有在确属历史证据时才可保留在 current records 中。

## 当前状态

不要从本文件推断当前 release、兼容性或生产就绪度。请使用以下权威文档：

- `docs/current/README.md`
- `docs/current/AEGIS_HOST_COMPATIBILITY_MATRIX_SNAPSHOT.md`
- `docs/current/AEGIS_METHOD_PACK_RELEASE_CHECKLIST.md`
- `docs/current/AEGIS_KNOWN_LIMITATIONS.md`
