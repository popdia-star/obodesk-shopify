# OboDesk Shopify Read-Only Architecture Audit - 2026-06-18

## 1. Executive Summary

- 项目根目录为 `D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify`，独立于 `AI-Commerce-OS`，符合双仓库边界。
- 仓库具备继续承载 Validation 工作的基本条件，但仅适合文档、证据记录和人工核验；当前不适合任何整体 Theme 同步或自动化数据写入。
- Git 工作区在审计时干净，当前分支为 `master`，但本地比 `origin/master` 超前 3 个提交；远程同步状态未联网复核。
- 本地正式主题基于 Shopify Skeleton Theme `0.1.0`，不是 Dawn；包含多个 OboDesk 自定义 section。
- 本地正式主题与最近保存的线上快照不一致，存在全量同步 P0 风险。
- `rollback-backups/` 内存在多套完整或接近完整的主题副本，误用风险较高。
- Validation 资料结构基本完整，但实际市场证据尚未形成。
- 当前应先固化审计报告、Shopify 操作红线和 Validation 日志入口，不应先整理、移动目录或继续修改 Theme。

## 2. Scope and Guardrails

本次架构审计仅检查本地文件系统和 Git 元数据。

审计阶段未执行：

- Shopify CLI、theme pull、theme push、theme deploy 或 theme publish。
- Shopify 后台、PageFly、商品、集合、页面、导航、支付、物流或库存操作。
- Product Center、飞书或 CSV 导入。
- 文件创建、修改、删除、移动或重命名。
- Git commit、push、fetch、pull、reset 或 checkout。
- 线上 Live Theme 当前状态验证。

报告中提到的 Live Theme 名称和 Theme ID 仅来自仓库内历史审计记录，不代表 2026-06-18 已实时确认。

## 3. Repository / Workspace Status

| 项目 | 结果 |
| --- | --- |
| 项目根目录 | `D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify` |
| `.git` | 存在 |
| 当前分支 | `master` |
| 远程仓库 | `https://github.com/popdia-star/obodesk-shopify.git` |
| 审计时工作区 | 干净 |
| 分支关系 | `master...origin/master [ahead 3]` |
| 本地 HEAD | `f72d26c` |
| 远程实时状态 | 未 fetch，未联网复核 |

未推送提交包括：

1. `1a1e0a0` — Validation operating index。
2. `09ef332` — Monitor Riser validation materials。
3. `f72d26c` — Validation evidence organization。

`rollback-backups/`、`references/` 和 `.codex-lark-*` 被 `.gitignore` 忽略，因此 Git clean 不代表这些目录已被版本控制保护，也不能证明其中内容与线上状态一致。

## 4. Directory Map

| 目录 | 用途与判断 | 建议 |
| --- | --- | --- |
| `theme/obodesk-theme/` | 本地正式 Shopify Theme | 保留只读使用；禁止整体推送 |
| `docs/` | INDEX、SOP、事实核验、Validation 计划和历史日志 | 继续使用 |
| `data/` | MVP5、商品事实、Product Center review 和 14 天日志 CSV | 继续使用，但禁止直接导入 |
| `rollback-backups/` | 历史恢复证据和主题快照 | 保留但隔离，不得作为正式 Theme 源 |
| `references/` | 店铺设计等背景参考 | 不作为当前事实源 |
| `scripts/` | 当前为空 | Validation 阶段不要扩展自动化 |
| `ai-workflows/` | 当前为空 | 暂不使用 |
| `.codex-lark-*` | 工具缓存 | 不应进入事实链 |
| `obodesk-shopify_live-theme-check/` | 仓库外临时 Theme 检查目录 | 高误用风险，后续由人工确认归档 |

现在不建议整理或移动目录。多个现有文档引用当前路径，主题快照仍具有事故证据和恢复价值。

## 5. Shopify Theme and Page Risk Review

- 本地正式 Theme 目录为 `theme/obodesk-theme/`。
- `config/settings_schema.json` 标识为 Shopify Skeleton Theme `0.1.0`。
- 未发现 Dawn Theme 标识。
- 存在多个 OboDesk 自定义 sections，包括 hero、core system、kits、lighting、why、featured products、header 和 footer。
- 本地 Theme 与历史线上快照不一致。
- PageFly snippet 只存在于线上快照和预览备份，本地正式 Theme 缺失。
- 当前只能确认存在 PageFly 残留或集成痕迹，不能确认其在当前正式页面是否实际生效。
- 最大风险不是代码本身，而是操作者选错目录、Theme ID、预览链接或同步范围。

禁止整体同步的关键文件：

- `config/settings_data.json`
- `templates/*.json`
- `sections/*-group.json`
- `sections/page.liquid`
- `snippets/pagefly-main-js.liquid`
- `locales/en.default*.json`

为避免不同账号看到不同首页，后续应执行以下控制：

1. 每次 QA 都记录店铺域名、Published Theme 名称和 Theme ID。
2. 使用无预览参数的正式域名测试，并另用无痕窗口验证。
3. 清除 Shopify Theme Preview cookie。
4. 检查 URL 是否含 `preview_theme_id`。
5. 分别确认 PageFly 页面发布目标、Theme Editor 预览目标和正式 Published Theme。
6. 每次只允许一个未发布 Preview Theme 作为候选。
7. 禁止从本地正式 Theme 目录进行全量 push。
8. 发布前后保留桌面端、移动端、不同会话的截图及 Theme ID。

## 6. Product Data and Validation Assets Review

### MVP5

MVP5 包括：

1. Signature Monitor Riser
2. Premium Wool Felt Desk Mat
3. RGB Monitor Light Bar
4. 8-in-1 USB-C Hub
5. RGB Podcast Dynamic Microphone

`data/obodesk_mvp_product_fact_verification_today.csv` 是人工核验工作表。

`data/obodesk_mvp5_product_center_sync_review_draft.csv` 是 `Review Draft Only`，不能作为正式导入源。

### Signature Monitor Riser

- 当前 Validation 主产品。
- 已确认标题、Handle、Product ID、SKU、Variant ID、尺寸、颜色和价格。
- 仍缺失精确材质、承重、净重、包装内容、原产国和供应商截图归档。
- 应在开始公开内容测试前完成产品事实核验。

### Desk Mat

- 已确认尺寸、厚度、颜色等部分事实。
- Shopify 当前名称、Handle 和标签仍含 `wool`。
- 自然羊毛、羊毛含量、防水、耐污、易清洗等均未被证实。
- 不应在 Monitor Riser Validation 中作为主要卖点。

### Cable Management

- 当前 MVP5 中没有独立 Cable Management 商品记录。
- 最接近的是 8-in-1 USB-C Hub 的 connectivity/cable simplification 场景。
- 如果 Cable Management 被视为独立产品线，需要人工确认正式 SPU、SKU 和商品身份。

### Audio Input

- 对应 RGB Podcast Dynamic Microphone。
- 型号、连接方式和部分包装信息已有供应商依据。
- 音频频响、灵敏度、阻抗、SPL、采样参数和材质等仍缺失。
- 不能使用 studio-grade、noise cancellation、zero latency 等表述。

### Monitor Riser 14-Day Validation

已存在：

- 14 天 Validation 计划。
- Day 1 Claim Review。
- Product Fact Check。
- Validation Content V1。
- Cold Visitor Checklist。
- Market Evidence Log。
- 14 天 CSV 日志。

当前状态：

- CSV 有计划行，但 TikTok、PDP、加购、Checkout、订单等指标为空。
- Market Evidence Log 是空白模板。
- 当前只有 Validation 准备资料，尚无实际市场验证结果。

## 7. Logs and Decision Records

当前记录入口包括：

- `docs/INDEX.md`
- `docs/DAILY_WORKFLOW.md`
- `docs/OBODESK_ADVERSARIAL_REVIEW_LOG.md`
- `docs/PRODUCT_CENTER_V1_LOG.md`
- `docs/OBODESK_LIVE_THEME_DIFF_AUDIT_2026-06-03.md`
- `docs/OBODESK_WORKSPACE_STRUCTURE_AUDIT_2026-05-20.md`
- `data/obodesk_monitor_riser_14day_validation_log_draft.csv`

判断：

- `docs/INDEX.md` 应继续作为总入口。
- `docs/DAILY_WORKFLOW.md` 已混合大量 Build 历史，继续膨胀风险较高。
- 建议后续使用 `docs/work-log/YYYY/YYYY-MM-DD.md` 按日期拆分记录。
- Build → Validation 已记录在 `docs/INDEX.md`、`docs/DAILY_WORKFLOW.md` 和 Monitor Riser Validation 相关文件中。

## 8. Risk Register

### P0

- 本地 Theme 不是线上完整真相，全量同步可能覆盖在线页面、页脚和 Theme Editor 配置。
- 多个 Theme 快照可被误当作发布目录。
- 直接同步 JSON 配置文件可能覆盖首页、导航、页脚、集合页和商品页结构。
- Product Center review CSV 可能被误导入。
- Git clean 可能被误解为全部资产安全。

### P1

- Validation 尚无真实市场证据。
- Monitor Riser 核心事实不完整。
- Desk Mat 仍含未证实的 wool 表述。
- 正式 Product Center、仓库 CSV 和外部 SPU/SKU 模板的版本关系不明确。
- Cable Management 没有明确独立商品身份。
- 本地 tracking remote 未实时 fetch，三个 Validation 提交尚未同步。

### P2

- Theme README 仍是 Shopify Skeleton 原始说明。
- 缺少根目录 README、CHANGELOG 和独立 DECISION_LOG。
- `DAILY_WORKFLOW.md` 同时承担过多职责。
- `scripts/`、`ai-workflows/` 和多个缓存目录为空或仅占位。
- 存在旧临时目录和空目录。
- 外部 Product Center 模板存在正式目录与备份目录两份副本。

## 9. Recommended Next Actions

### Do Next

1. 保存本报告。
2. 使用 `docs/OBODESK_SHOPIFY_OPERATION_RED_LINES.md` 作为 Theme 操作前红线入口。
3. 明确 Validation 日志入口。
4. 对 Monitor Riser 进行人工产品事实核验。
5. 人工确认 Feishu 正式 Product Center 与外部模板之间的版本关系。
6. 真实 Validation 开始后，只记录可追溯的市场证据。
7. 任何未来 Theme 工作前，先只读确认当前 Published Theme ID 和 PageFly 发布目标。

### Do Not Do Yet

- 不要整理、移动、删除或重命名 Theme 快照。
- 不要执行全量 Theme pull 后覆盖本地正式目录。
- 不要执行 batch theme push。
- 不要从 `rollback-backups/` 直接发布。
- 不要导入任何当前 CSV。
- 不要创建 Shopify metafields。
- 不要扩展 Product Center、SKU 矩阵、产品分类或自动化。
- 不要把 Validation 准备材料描述为市场验证结果。

### Need Human Confirmation

- 当前真正 Published Theme 的名称和 Theme ID。
- PageFly 是否仍在当前正式首页或其他页面生效。
- 三个未推送 Validation 提交是否批准同步到远程。
- 哪个外部 Product Center 文件是当前正式版本。
- Monitor Riser 的供应商或采购证据位置。
- Cable Management 是否应当作为独立产品。

## 10. Evidence

实际检查的主要文件和资产包括：

- `docs/INDEX.md`
- `docs/DAILY_WORKFLOW.md`
- `docs/OBODESK_THEME_RELEASE_AND_ROLLBACK_SOP.md`
- `docs/OBODESK_LIVE_THEME_DIFF_AUDIT_2026-06-03.md`
- `docs/OBODESK_WORKSPACE_STRUCTURE_AUDIT_2026-05-20.md`
- `docs/OBODESK_MONITOR_RISER_14DAY_VALIDATION_PLAN_DRAFT.md`
- `docs/OBODESK_MONITOR_RISER_FACT_CHECK_2026-06-13.md`
- `docs/OBODESK_MONITOR_RISER_DAY1_CLAIM_REVIEW_DRAFT.md`
- `docs/OBODESK_MARKET_EVIDENCE_LOG_V1.md`
- `docs/PRODUCT_CENTER_V1_LOG.md`
- `data/README.md`
- `data/` 下 CSV 文件
- `theme/obodesk-theme/`
- `rollback-backups/`
- 外部 Product Center 模板目录
- Monitor Riser 部分本地产品图片

审计阶段使用的只读命令类型：

- `Get-ChildItem`
- `Get-Content`
- `rg`
- `Import-Csv`
- `Get-FileHash`
- `git status`
- `git remote -v`
- `git branch --show-current`
- `git log`
- `git diff origin/master..HEAD`
- `git ls-files`

本次为只读审计，未修改 Theme 文件、未修改 data 文件、未提交 commit、未 push、未触碰 Shopify 后台。
