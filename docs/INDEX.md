# OboDesk Documentation Index

Updated: 2026-05-20

Purpose: this index is the entry point for OboDesk project documentation. It tells future operators and agents which files to read first, which files are current, which files are draft-only, and which files must not be treated as official Product Center or Shopify data.

## Read First

For any OboDesk product, storefront, Product Center, content, or automation task, read these first:

1. `docs/OBODESK_MVP_SCOPE.md`
2. `docs/OBODESK_PROBLEM_EVIDENCE_MAP.md`
3. `docs/OBODESK_AGENTIC_WORKFLOW_DESIGN.md`
4. `docs/OBODESK_ADVERSARIAL_REVIEW_LOG.md`
5. `docs/OBODESK_AI_NATIVE_STARTUP_METHOD.md`

Current stage: evidence-based MVP. The current priority is to collect real market evidence, not to expand automation or product scope.

## Source Of Truth Priority

When sources conflict, use this priority order:

1. Shopify commerce facts: product IDs, variant IDs, handles, prices, inventory, publication status, product URLs, order data, checkout behavior.
2. Supplier / physical evidence: supplier pages, supplier sheets, packaging, product images, certifications, direct supplier confirmation, physical samples.
3. Product Center reviewed records: human-reviewed Feishu / Product Center fields and review statuses.
4. Local review drafts: CSV review drafts, safe PDP drafts, sync drafts, Codex validation reports.
5. AI draft content: generated summaries, PDP drafts, scripts, hypotheses, recommendations.

AI drafts and local review drafts are not official facts by themselves.

## MVP Working Principles

- Do not treat page completion, theme polish, or checkout operability as PMF.
- Do not treat drafts as official data.
- Do not treat AI output as verified fact.
- Do not automate before the process has been manually run, reviewed, and stabilized.
- All Product Center writes, Shopify publication changes, Shopify metafields, PDP publication, and CSV imports require human review.
- Weak evidence is only an unvalidated hypothesis. It can justify a small validation action, not a launch-stage decision.

## Current / 当前主线

These files define the current evidence-based MVP operating system and should be actively maintained.

| File | Purpose | Status |
| --- | --- | --- |
| `docs/OBODESK_MVP_SCOPE.md` | Defines current MVP scope, non-goals, launch evidence threshold, and pivot review cadence. | Current |
| `docs/OBODESK_PROBLEM_EVIDENCE_MAP.md` | Tracks target users, scenarios, pain points, alternatives, evidence strength, and next validation actions. | Current |
| `docs/OBODESK_AGENTIC_WORKFLOW_DESIGN.md` | Defines roles for Codex, Shopify, Product Center, Feishu, n8n, TikTok content, and human review. | Current |
| `docs/OBODESK_ADVERSARIAL_REVIEW_LOG.md` | Records adversarial reviews and continue / pause / modify / return-to-idea decisions. | Current |
| `docs/DAILY_WORKFLOW.md` | Long-running project work log. Use for historical context and recent status checks, but verify current state before acting. | Current log / historical mix |
| `docs/OBODESK_THEME_RELEASE_AND_ROLLBACK_SOP.md` | OboDesk Shopify theme release, preview, single-file deployment, and emergency rollback SOP. | Current operating doc |
| `docs/OBODESK_LIVE_THEME_DIFF_AUDIT_2026-06-03.md` | Live Theme and local formal theme directory difference audit, forbidden sync list, and single-file release allowlist. | Current audit |

## Methodology / 方法论

These files provide upper-level context and decision principles.

| File | Purpose | Status |
| --- | --- | --- |
| `docs/OBODESK_AI_NATIVE_STARTUP_METHOD.md` | OboDesk-specific AI-native startup method and current stage judgment. | Methodology |
| `docs/decision_hypothesis_loop.md` | Hui OS decision-hypothesis-review loop for long-feedback entrepreneurship work. | Methodology |

## Product Center / 商品事实核验

These files define Product Center workflow, field rules, status rules, and fact verification boundaries.

| File | Purpose | Status |
| --- | --- | --- |
| `docs/PRODUCT_CENTER_V1_SOP.md` | Product Center v1.0 operating model and Shopify-first workflow. | Current operating doc |
| `docs/PRODUCT_CENTER_V1_LOG.md` | Product Center v1.0 closure status, operating boundaries, and next direction. | Current status log |
| `docs/PRODUCT_CENTER_STATUS_FLOW.md` | Recommended Product Center status fields and transition rules. | Current design |
| `docs/DAILY_PRODUCT_LAUNCH_SOP.md` | Daily product launch workflow from Shopify to Product Center review. | Current operating doc |
| `docs/OBODESK_PRODUCT_FACT_VERIFICATION_FIELD_GUIDE.md` | Field guide for manual product fact verification CSV. | Current guardrail |
| `docs/AI_SHOPPING_READINESS_FIELDS_V1.md` | P0 fields for AI-friendly PDP content planning before Shopify metafields. | Planning doc |

## Draft Only / 草稿，仅供审阅

These files are review materials only. Do not directly import, publish, sync, or use as storefront content without human approval.

| File | Purpose | Restriction |
| --- | --- | --- |
| `docs/OBODESK_MVP5_SAFE_PDP_DRAFT_V0.1.md` | Safe PDP copy draft for five MVP products. | Draft only. Do not publish to Shopify, import into Product Center, or create Shopify metafields from it. |
| `docs/OBODESK_MVP5_PRODUCT_CENTER_SYNC_DRAFT_V0.1.md` | Product Center field sync review draft for MVP5. | Manual review only. Do not write formal Product Center data from it. |
| `docs/OBODESK_DESK_MAT_SAFE_SHOPIFY_UPDATE_2026-05-31.md` | Human Shopify Admin update packet for safer Desk Mat title, PDP copy, SEO, and URL handling. | Manual Shopify Admin update packet only. Do not automate or import. |
| `data/obodesk_mvp5_product_center_sync_review_draft.csv` | CSV version of Product Center sync review draft. | `Ready_To_Import = No`; `Product_Center_Write_Status = Review Draft Only`. Do not import into formal Product Center. |
| `data/obodesk_mvp_product_fact_verification_today.csv` | Current manual product fact verification worksheet. | Manual verification only. Do not import into Product Center, sync to Shopify metafields, or use for frontend PDP display until approved. |
| `data/obodesk_ai_pdp_p0_template.csv` | First-pass AI PDP P0 content draft. | Draft only. Do not treat as verified product fact or PDP copy. |

## Historical / 历史记录

These files are useful for context but should not override current source-of-truth rules.

| File | Purpose | Note |
| --- | --- | --- |
| `docs/DAILY_WORKFLOW.md` | Full operating history for theme, storefront, Product Center, and AI Shopping Readiness work. | Large mixed-status log. Confirm current state before using as input. |
| `data/obodesk_mvp_product_fact_checklist.csv` | Early product fact checklist. | Contains `TBD` / `Pending` fields. Use as historical template, not current fact source. |

## Reference / 外部参考

These files are background material only.

| File | Purpose | Note |
| --- | --- | --- |
| `docs/reference/FOUNDERS_PLAYBOOK_CN_EXTRACT.md` | Source excerpt used to build OboDesk AI-native startup method. | Reference only. |
| `references/OboDesk 新完整店铺设计方案0422版.pdf` | Earlier OboDesk full store design reference. | External design reference. Confirm current product direction before using. |

## Risk / 容易误用文件

These files are easy to misuse because they look complete or import-ready.

| File | Misuse risk | Required handling |
| --- | --- | --- |
| `data/obodesk_mvp5_product_center_sync_review_draft.csv` | Looks like a Product Center import file. | Do not import. It is review-only until human approval changes readiness. |
| `data/obodesk_mvp_product_fact_verification_today.csv` | Contains partially verified product facts. | Do not treat as formal Product Center data or Shopify metafield source. |
| `data/obodesk_ai_pdp_p0_template.csv` | Contains AI-drafted PDP fields that may include unverified assumptions or old handles. | Use only as first-pass draft context. |
| `docs/OBODESK_MVP5_PRODUCT_CENTER_SYNC_DRAFT_V0.1.md` | Looks like a complete sync plan. | Keep as manual review draft. Do not write formal records from it directly. |
| `docs/OBODESK_MVP5_SAFE_PDP_DRAFT_V0.1.md` | Looks publishable because it is polished. | Do not publish or convert to metafields until facts and claims are approved. |
| `.codex-lark-read-json/` | Local connector/Codex read artifact. | Do not use as project source-of-truth. |

## Shopify Theme / Code

Theme files live under:

```text
theme/obodesk-theme/
```

Before any theme work, read:

1. `theme/obodesk-theme/AGENTS.md`
2. `docs/OBODESK_MVP_SCOPE.md`
3. `docs/OBODESK_AGENTIC_WORKFLOW_DESIGN.md`

Current rule: do not modify product form, variant selector, cart, checkout, payment, or PDP metafield rendering unless the task explicitly approves that scope and verification path.

## Next Suggested Index Work

Recommended next step: add `data/README.md` to document CSV purpose, import restrictions, source-of-truth priority, and which files are draft-only.

Do not create `data/README.md` in this round unless explicitly requested.
