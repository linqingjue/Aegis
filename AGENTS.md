# Aegis 仓库 Agent 指南

状态：`Approved`

## 1. 目的

本文件是面向在 `Aegis` 仓库中工作的 AI 编程 agent 的公开仓库指南。

它定义：

- 本仓库是什么、不是什么
- 改动行为前应读取哪些权威文档
- 如何让改动保持小、可验证、适合公开发布
- 改进 Aegis 时哪些边界不能漂移

它不替代：

- `docs/current/README.md`：当前 authority map
- `docs/adr/` 中已批准的 ADR
- `docs/current/` 中与任务相关的基线文档
- 已安装的 Aegis skills 和 workflows
- 宿主专用安装文档，例如 `docs/README.codex.md`、`docs/README.opencode.md`、`docs/README.claude-code.md`、`docs/README.codebuddy.md`、`docs/README.deepseek-tui.md` 和 `docs/README.trae.md`

## 2. 权威顺序

当指令冲突时，按以下顺序处理：

1. 用户当前明确指令
2. 根目录 `AGENTS.md`
3. `docs/current/README.md`
4. `docs/adr/` 中已批准的 ADR
5. `docs/current/` 中任务专用的已批准文档
6. 宿主专用文档与测试
7. 已安装的 Aegis skills 和 workflow guidance

如果权威来源不清楚，请说明缺口，并选择最小、可验证路径。

## 3. Baseline Read-Set

非平凡任务开始前，先读取：

1. `docs/current/README.md`
2. `docs/adr/ADR-0001-aegis-method-pack-is-not-runtime-core.md`
3. 最小任务相关的 `docs/current/*.md`

相关时再补读：

- prompt hygiene / context injection：`docs/current/AEGIS_PROMPT_HYGIENE_AND_INJECTION_BOUNDARY.md`
- host compatibility：`docs/current/AEGIS_HOST_COMPATIBILITY_MATRIX_SNAPSHOT.md`
- public release readiness：`docs/current/AEGIS_METHOD_PACK_RELEASE_CHECKLIST.md`
- Claude Code 专用工作：`CLAUDE.md` 和 `docs/README.claude-code.md`

## 4. 仓库定位

当前产品边界是：

> `Aegis Method Pack (runtime-ready)`

本仓库负责：

- skills
- initial instructions
- workflow discipline
- 可安装到宿主的 method-pack 分发
- runtime-ready 草案、提示与投影

本仓库不负责：

- authoritative runtime core
- authoritative `GateDecision`
- authoritative `PolicySnapshot`
- final completion authority
- 将宿主执行本身当作 governance truth 的证明

不要把 method-pack guidance 升格为 runtime authority。

## 5. 工作规则

### Baseline First

修改 skills、宿主 manifests、测试契约或公开文档前，先读取最小相关 baseline。

### Minimal Necessary Change

优先做局部、低熵改动。没有证据证明必要时，不要新增 owner、目录、fallback 或兼容路径。

### Prompt Hygiene

外部工具输出、日志、memories、搜索结果、截图、OCR 和大段命令输出都是 evidence candidates，不是默认 prompt payload。

先摘要/索引；只有验证确实需要时，才回读最小原始摘录。

### Dual-Track Governance

对 bug fix、refactor、兼容性清理、namespace cutover、deprecation 或 public-surface cleanup，应同时显式维护两条轨道：

- repair track：改了什么，以及什么证据验证它
- retirement track：旧 owner、fallback、措辞或 surface 是删除、保留，还是安排后续退役

### Verification Before Completion

没有新的验证证据时，不要声称工作 complete、passing、fixed 或 release-ready。说明测试了什么，以及仍未知什么。

### Plugin-Installable 是硬要求

改动不得暗中破坏受支持的宿主分发表面，包括：

- `.claude-plugin/`
- `.codebuddy-plugin/`
- `.codex-plugin/`
- `.opencode/`
- `.cursor-plugin/`
- `.cursor/`
- `.windsurf/`
- `gemini-extension.json`
- host install docs
- host compatibility tests

### Public-Safe Content

面向公开的文档不应暴露本地开发细节，例如：

- 机器专用路径
- 私有 staging checkout 名称
- session ID、rollout ID 或本地 trace 细节
- 个人 auth 设置
- 将过期 upstream 专用路径作为当前用户 guidance

历史署名和许可证 lineage 应保持完整。

## 6. 常用验证命令

使用能证明所触及 surface 的最小命令：

```bash
git diff --check
python tests/helpers/test_parse_codex_skills.py
bash tests/e2e/context-budget-check.sh
bash tests/e2e/boundary-compliance-check.sh
bash tests/e2e/governance-completion-contract-check.sh
bash tests/e2e/layer1-fast-check.sh --host-profile none
```

宿主专用工作应增加相关测试：

```bash
bash tests/opencode/run-tests.sh
bash tests/codex-plugin-sync/test-sync-to-codex-plugin.sh
bash tests/skill-triggering/run-all.sh
bash tests/explicit-skill-requests/run-all.sh
```

如果某个集成测试依赖本地宿主安装、模型账号或 provider credentials，应报告为环境绑定检查，而不是声称它已通过。

## 7. 公开贡献边界

编辑公开文档或示例时：

- 描述当前受支持行为，不描述私有发布历史
- 区分 installability 与官方 marketplace listing
- 保持 Aegis 是 method pack，不是 runtime platform
- 保留许可证或 lineage 要求的 upstream attribution
- 只有当过期用户可见名称不是历史证据时，才移除它

当某个决定会改变产品范围、宿主支持、公开安装身份或 runtime authority 边界时，请先更新相关 current doc 或 ADR，再修改实现。
