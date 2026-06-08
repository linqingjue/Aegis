# Aegis 当前文档

状态：`Approved`

## 1. 目的

本目录保存 `Aegis Method Pack` 当前公开基线。

它刻意保持较小范围。内部实现记录、迁移计划、私有 smoke 记录、cutover 清单和仅本地使用的审计轨迹，不应进入这个公开 current surface。

## 2. 仓库边界

当前仓库是：

> `Aegis Method Pack (runtime-ready)`

本仓库负责：

- skills 与工作流纪律
- 可安装到宿主的 method-pack 分发
- runtime-ready 草案、提示与投影
- 用户和贡献者需要的公开文档

本仓库不负责：

- authoritative runtime core
- authoritative `GateDecision`
- authoritative `PolicySnapshot`
- final `completion authority`

## 3. 权威顺序

当公开文档发生冲突时，按以下顺序处理：

1. `AGENTS.md`
2. `docs/current/README.md`
3. `docs/adr/` 中已批准的 ADR
4. `docs/current/` 中与任务相关的文档
5. 宿主专用文档，例如 `docs/README.codex.md`、`docs/README.opencode.md`、`docs/README.claude-code.md`、`docs/README.cc-gui.md`、`docs/README.codebuddy.md`、`docs/README.deepseek-tui.md`、`docs/README.trae.md`、`docs/README.copilot.md`、`docs/README.qoder.md`、`docs/README.pi.md`、`docs/README.openclaw.md` 和 `docs/README.hermes-agent.md`
6. tests 与 fixtures

## 4. 公开 current 基线

公开 current 文档集包括：

- `docs/current/AEGIS_TARGET_STATE.md`
- `docs/current/AEGIS_PRODUCT_BASELINE.md`
- `docs/current/AEGIS_PROCESS_BASELINE.md`
- `docs/current/AEGIS_WORKFLOW_GUIDE.md`
- `docs/current/AEGIS_WORKFLOW_GUIDE_ZH.md`
- `docs/current/AEGIS_ACTIVATION_MODE.md`
- `docs/current/AEGIS_TDD_MODE.md`
- `docs/current/AEGIS_PROMPT_HYGIENE_AND_INJECTION_BOUNDARY.md`
- `docs/current/AEGIS_RULE_LAYERING.md`
- `docs/current/AEGIS_TRIGGER_HEALTH_BASELINE.md`
- `docs/current/AEGIS_WORKFLOW_QUALITY_BASELINE.md`
- `docs/current/AEGIS_DUAL_TRACK_GOVERNANCE.md`
- `docs/current/AEGIS_ADR_AUTO_BACKFILL.md`
- `docs/current/AEGIS_ARTIFACT_SCHEMA_BASELINE.md`
- `docs/current/AEGIS_RUNTIME_READY_BOUNDARY.md`
- `docs/current/AEGIS_METHOD_PACK_RELEASE_CHECKLIST.md`
- `docs/current/AEGIS_HOST_COMPATIBILITY_MATRIX_SNAPSHOT.md`
- `docs/current/AEGIS_KNOWN_LIMITATIONS.md`
- `docs/adr/ADR-0001-aegis-method-pack-is-not-runtime-core.md`

## 5. 文档职责

`AEGIS_TARGET_STATE.md`
: 用一页说明本仓库想成为的目标状态。

`AEGIS_PRODUCT_BASELINE.md`
: 产品边界、负责的 surface 和非目标。

`AEGIS_PROCESS_BASELINE.md`
: method 层工作流基线、证据纪律，以及 `Design Defect` / `Implementation Drift` 等共享术语。

`AEGIS_WORKFLOW_GUIDE.md`
: 工作流程说明的兼容文件名；项目默认中文化后，其内容应与中文说明保持一致或指向中文说明。

`AEGIS_WORKFLOW_GUIDE_ZH.md`
: 面向用户和贡献者的中文工作流程说明，解释当前 Aegis workflow，但不添加 runtime authority。

`AEGIS_ACTIVATION_MODE.md`
: `auto` 和 `explicit` activation mode 的语义。

`AEGIS_TDD_MODE.md`
: 自动 test-first 路由中 `auto` 和 `off` TDD mode 的语义。

`AEGIS_PROMPT_HYGIENE_AND_INJECTION_BOUNDARY.md`
: 有界上下文摄取、证据索引，以及日志/输出卫生。

`AEGIS_RULE_LAYERING.md`
: method、host 和 repo 规则分层。

`AEGIS_TRIGGER_HEALTH_BASELINE.md`
: 针对“已安装但没有稳定触发正确 skill”的触发链路诊断，包括安装、发现、activation、路由、执行深度和 false-positive 层。

`AEGIS_WORKFLOW_QUALITY_BASELINE.md`
: 高频 workflow 的质量基线，包括紧凑输出契约、代表性样本、fast-path cheapness、证据新鲜度、artifact 稳定性、workspace laziness 和 authority boundary。

`AEGIS_DUAL_TRACK_GOVERNANCE.md`
: repair track 加 retirement track 的治理规则。

`AEGIS_ADR_AUTO_BACKFILL.md`
: 从 work、plan、spec 和 verification evidence 中在完成时回填 ADR，并同步 ADR/baseline 规则。

`AEGIS_ARTIFACT_SCHEMA_BASELINE.md`
: 最小 runtime-ready artifact 形态。

`AEGIS_RUNTIME_READY_BOUNDARY.md`
: method pack 可以输出什么，以及只有未来 runtime core 才能决定什么。

`AEGIS_METHOD_PACK_RELEASE_CHECKLIST.md`
: 最小发布门禁和验证回读。

`AEGIS_HOST_COMPATIBILITY_MATRIX_SNAPSHOT.md`
: 当前宿主兼容性快照和证据边界。

`AEGIS_KNOWN_LIMITATIONS.md`
: 当前限制和保留的兼容性边界。

## 6. 本地归档规则

`docs/archive/` 仅限本地使用，并被 git 忽略。

它可用于实现历史、内部迁移记录、私有 staging notes，以及不应随公开仓库发布的旧 cutover material。

不要从公开 README、宿主安装文档或发布说明中引用 `docs/archive/`。

## 7. 更新规则

当改动影响公开行为、宿主安装、发布门禁、runtime-ready artifacts，或 method-pack/runtime-core 边界时，应先更新最小相关 current 文档，再修改实现。

如果某份文档只适合作为过程证据，请不要放入 `docs/current`。
