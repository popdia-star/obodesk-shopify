# OboDesk Workspace Structure Audit 2026-05-20

## 1. 当前目录结构概览

检查根目录：

`D:\My-AiOS\10_Workspace\WORK`

顶层可见结构：

```text
WORK/
├─ 05_AI_提示词与脚本/
├─ cache/
├─ exports/
├─ logs/
├─ obodesk/
├─ plans/
├─ shopify-projects/
│  ├─ obodesk-shopify/
│  └─ obodesk-shopify_live-theme-check/
├─ _inbox/
├─ 热点抓取/
├─ README_文件系统说明书.md
├─ SOP_42条软件迁移安装说明书_最终版_方案B.txt
└─ 抢救_整理报告_20260126.md
```

当前 OboDesk 主工作目录应继续保持为：

```text
D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify
```

主项目结构：

```text
obodesk-shopify/
├─ .codex-lark-field-json/
├─ .codex-lark-read-json/
├─ .codex-lark-record-json/
├─ .git/
├─ ai-workflows/
├─ data/
├─ docs/
│  └─ reference/
├─ references/
├─ scripts/
└─ theme/
   └─ obodesk-theme/
```

## 2. OboDesk 核心资产分布

### Shopify 项目主目录

`shopify-projects/obodesk-shopify/`

这是当前主线目录，包含 docs、data、theme、Product Center 草稿和证据化 MVP 文档。

### Shopify Theme

`theme/obodesk-theme/`

标准 Shopify theme 结构完整：

```text
assets/
blocks/
config/
layout/
locales/
sections/
snippets/
templates/
```

主要代码文件集中在：

```text
theme/obodesk-theme/sections/
theme/obodesk-theme/templates/
theme/obodesk-theme/assets/critical.css
```

### 方法论与长期上下文

```text
docs/OBODESK_AI_NATIVE_STARTUP_METHOD.md
docs/reference/FOUNDERS_PLAYBOOK_CN_EXTRACT.md
docs/OBODESK_MVP_SCOPE.md
docs/OBODESK_PROBLEM_EVIDENCE_MAP.md
docs/OBODESK_AGENTIC_WORKFLOW_DESIGN.md
docs/OBODESK_ADVERSARIAL_REVIEW_LOG.md
docs/INDEX.md
```

### Product Center / 商品事实核验

```text
docs/PRODUCT_CENTER_V1_SOP.md
docs/PRODUCT_CENTER_V1_LOG.md
docs/PRODUCT_CENTER_STATUS_FLOW.md
docs/DAILY_PRODUCT_LAUNCH_SOP.md
docs/OBODESK_PRODUCT_FACT_VERIFICATION_FIELD_GUIDE.md
data/obodesk_mvp_product_fact_verification_today.csv
data/obodesk_mvp5_product_center_sync_review_draft.csv
data/README.md
```

## 3. 当前主线文件清单

当前任务和后续 Agent 应优先读取：

```text
docs/INDEX.md
docs/OBODESK_MVP_SCOPE.md
docs/OBODESK_PROBLEM_EVIDENCE_MAP.md
docs/OBODESK_AGENTIC_WORKFLOW_DESIGN.md
docs/OBODESK_ADVERSARIAL_REVIEW_LOG.md
docs/OBODESK_AI_NATIVE_STARTUP_METHOD.md
docs/DAILY_WORKFLOW.md
data/README.md
```

Product Center / 商品事实相关主线：

```text
docs/OBODESK_PRODUCT_FACT_VERIFICATION_FIELD_GUIDE.md
docs/OBODESK_MVP5_PRODUCT_CENTER_SYNC_DRAFT_V0.1.md
data/obodesk_mvp_product_fact_verification_today.csv
data/obodesk_mvp5_product_center_sync_review_draft.csv
```

## 4. 方法论文件是否可作为长期上下文

可以。

`docs/OBODESK_AI_NATIVE_STARTUP_METHOD.md` 已明确当前阶段为“证据化 MVP 阶段”，并包含总原则、固定工作流、反证优先、Agentic 编程护栏和自动化前置条件。

`docs/INDEX.md` 已成为当前文档入口，明确：

- Read First 文件；
- 事实源优先级；
- MVP 工作原则；
- Current / Methodology / Product Center / Draft Only / Historical / Reference / Risk 分类；
- Shopify theme 工作前置阅读文件。

`data/README.md` 已明确 CSV 使用边界，能防止误导入、误同步和误发布。

一个小问题：`docs/INDEX.md` 的 `Next Suggested Index Work` 仍写着建议新增 `data/README.md`，但该文件现在已经存在。后续可小修该段，但本轮未修改。

## 5. 临时 / 中间产物

以下属于临时或中间产物，不建议作为主事实源：

```text
.codex-lark-read-json/wiki-node-fact-check.json
.codex-lark-field-json/
.codex-lark-record-json/
```

`WORK\obodesk/` 中有：

```text
obodesk/创始人手册中文版.pdf
obodesk/docs/OBODESK_AI_NATIVE_STARTUP_METHOD.md
obodesk/docs/reference/FOUNDERS_PLAYBOOK_CN_EXTRACT.md
```

这些看起来是方法论导入过程中的早期工作区或副本。当前主线已在 `shopify-projects/obodesk-shopify/` 内建立完整上下文，因此 `WORK\obodesk/` 暂不应作为当前主输入源。

`shopify-projects/obodesk-shopify_live-theme-check/` 只有一个 `sections/header.liquid`，更像历史检查目录或临时 theme check 产物，不应作为当前 theme 主线。

## 6. 暂时不建议移动的文件

暂不建议移动：

```text
docs/DAILY_WORKFLOW.md
docs/OBODESK_MVP5_SAFE_PDP_DRAFT_V0.1.md
docs/OBODESK_MVP5_PRODUCT_CENTER_SYNC_DRAFT_V0.1.md
data/obodesk_mvp_product_fact_verification_today.csv
data/obodesk_mvp5_product_center_sync_review_draft.csv
```

原因：

- 当前 `docs/INDEX.md` 和 `data/README.md` 已经引用它们；
- 移动会增加路径变更风险；
- 当前阶段更需要稳定上下文，不需要先做目录重构。

也暂不建议移动：

```text
WORK/obodesk/
shopify-projects/obodesk-shopify_live-theme-check/
.codex-lark-*/
```

原因：需要人工确认它们是否有未迁移价值或是否应加入 `.gitignore` / 归档规则。

## 7. 未来可以归档的文件

可考虑未来归档，但现在不要执行：

```text
WORK/obodesk/
shopify-projects/obodesk-shopify_live-theme-check/
.codex-lark-read-json/
.codex-lark-field-json/
.codex-lark-record-json/
data/obodesk_mvp_product_fact_checklist.csv
```

其中 `data/obodesk_mvp_product_fact_checklist.csv` 已在 `data/README.md` 标记为 historical checklist / early verification template，不应作为当前事实源。

## 8. 今天下一步最建议推进的 1-3 个任务

1. 只读制定第一轮真实市场证据收集计划。

   基于 `docs/OBODESK_PROBLEM_EVIDENCE_MAP.md`，围绕 5 个 MVP 产品和 3 个核心场景，定义需要收集哪些用户问题证据、内容转化证据、加购 / 购买信号和客服反馈。

2. 小修 `docs/INDEX.md` 的状态说明。

   将 `Next Suggested Index Work` 中“建议新增 data/README.md”改为“已新增 data/README.md；下一步建议建立 Product Center 导入前人工审核清单”。这一步后续可做，本轮未执行。

3. 检查未提交 / 未跟踪文件状态。

   当前 `git status` 显示多份新文档和 CSV 仍未跟踪，且 `docs/DAILY_WORKFLOW.md`、`data/obodesk_mvp_product_fact_checklist.csv` 有修改。后续应由人工决定是否提交、拆分提交或继续保持工作区状态。

## 9. 本次检查未做任何修改

本次检查严格只读：

- 未创建 `docs/OBODESK_WORKSPACE_STRUCTURE_AUDIT_2026-05-20.md`。
- 未修改任何文件。
- 未移动文件。
- 未删除文件。
- 未重命名文件。
- 未修改代码。
- 未修改 Shopify theme。
- 未修改 Product Center 数据。
- 未修改 CSV。
- 未运行 Shopify 写入操作。
- 未调用 Shopify 写入 API。
- 未写入飞书 Product Center。
- 未执行 git commit。

说明：本文件是在用户明确要求将上述只读审计报告正式写入后创建的；除创建本报告文件外，未执行整理动作。
