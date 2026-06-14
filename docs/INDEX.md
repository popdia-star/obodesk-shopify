# OboDesk Documentation Index

Updated: 2026-06-14

Purpose: this index is the operating entry point for OboDesk after the Build stage. It tells future operators and agents what to read daily, what is only historical background, what is draft/review-only, and what must not be treated as official Shopify, Product Center, or product fact data.

## Current Stage

Current stage: `Build -> Validation`.

Shopify V1 now has a basic buying path foundation. OboDesk is entering the evidence-based MVP market validation stage instead of continuing broad site construction.

## Current Operating Focus

Current single operating focus: `Signature Monitor Riser 14-Day Validation`.

Core question: will real users understand, trust, click, add to cart, enter checkout, and ultimately pay USD 89 for the `Signature Monitor Riser`?

Validation work should produce evidence, not more build surface area.

## Source Of Truth Priority

When sources conflict, use this priority order:

1. Shopify commerce facts: product IDs, variant IDs, handles, prices, inventory, publication status, product URLs, order data, checkout behavior.
2. Supplier / physical evidence: supplier pages, supplier sheets, packaging, product images, certifications, direct supplier confirmation, physical samples.
3. Product Center reviewed records: human-reviewed Feishu / Product Center fields and review statuses.
4. Local review drafts: CSV review drafts, safe PDP drafts, sync drafts, Codex validation reports.
5. AI draft content: generated summaries, PDP drafts, scripts, hypotheses, recommendations.

AI drafts, CSV drafts, and Product Center draft files are not official facts by themselves.

## Current Operating Rules

- Do not treat page completion, theme polish, or checkout operability as PMF.
- Do not treat drafts as official data.
- Do not treat AI output as verified fact.
- Do not automate before a process has been manually run, reviewed, and stabilized.
- All Product Center writes, Shopify publication changes, Shopify metafields, PDP publication, and CSV imports require human review.
- Weak evidence is only an unvalidated hypothesis. It can justify a small validation action, not a launch-stage decision.

## Daily Execution Files

Read these first during the current Validation stage.

| File | Daily use | Status |
| --- | --- | --- |
| `docs/DAILY_WORKFLOW.md` | Long-running work log and current stage checkpoint. Use for recent status, but verify current state before action. | Current log / historical mix |
| `docs/OBODESK_MONITOR_RISER_14DAY_VALIDATION_PLAN_DRAFT.md` | 14-day validation plan for Monitor Riser buyer-intent signals. | Draft operating plan. No Shopify, Product Center, theme, or automation writes. |
| `docs/OBODESK_SHOPIFY_COLD_VISITOR_MANUAL_TEST_CHECKLIST_DRAFT.md` | Manual cold-visitor path checklist: Home -> Collection -> PDP -> Cart -> Checkout -> trust pages. | Manual checklist only. |
| `data/obodesk_monitor_riser_14day_validation_log_draft.csv` | Daily evidence log for content, traffic, PDP views, add-to-cart, checkout, orders, questions, objections, and decisions. | Draft log only. Do not import or automate. |
| `OBODESK_MARKET_EVIDENCE_LOG_V1.md` | Manual first-round market evidence log across MVP products and scenarios. | Manual validation log template. |
| `OBODESK_MONITOR_RISER_VALIDATION_CONTENT_V1.md` | Three TikTok validation content drafts for Monitor Riser interest testing. | Draft content. Requires human review before publishing. |

## Product Fact Sources

Use these to check product facts and claim boundaries.

| File | Role | Source status |
| --- | --- | --- |
| `MONITOR_RISER_FINAL_FACT_CHECK_2026-06-13.md` | Current local Monitor Riser final fact-check report. Confirms only dimensions; marks material, load capacity, product weight, package includes, and country of origin as missing. | Local reviewed fact-check report. Still requires human source confirmation before downstream sync. |
| `data/obodesk_mvp_product_fact_verification_today.csv` | MVP product fact verification worksheet with Shopify identity fields, partial supplier evidence, and missing fields. | Manual verification worksheet, not formal Product Center data. |
| `data/README.md` | Data directory usage boundary and CSV source-of-truth rules. | Current data guardrail. |
| `data/obodesk_mvp5_product_center_sync_review_draft.csv` | Product Center pre-import review CSV for MVP5. | Review draft only; `Ready_To_Import = No`; do not import or sync. |

Important rule: CSV files, AI PDP drafts, and Product Center draft files cannot be used directly as official product facts. They must be manually verified before they are used in PDP copy, ads, TikTok content, customer support answers, Shopify metafields, or Product Center formal records.

## Shopify Theme Safety

Theme files live under:

```text
theme/obodesk-theme/
```

Theme safety and recovery references:

| File or directory | Purpose | Status |
| --- | --- | --- |
| `docs/OBODESK_THEME_RELEASE_AND_ROLLBACK_SOP.md` | Required release, preview, single-file upload, backup, publish, and rollback procedure. | Current operating guardrail. |
| `docs/OBODESK_LIVE_THEME_DIFF_AUDIT_2026-06-03.md` | Live Theme vs local formal theme audit, forbidden sync list, and single-file allowlist. | Current audit. |
| `theme/obodesk-theme/` | Local formal Shopify theme directory. | Code source, not proof of online state. |
| `rollback-backups/` | Recovery previews, live theme audits, and rollback evidence directories. | Historical evidence / rollback material. |

Validation-stage theme rule: theme batch push remains frozen. Only if a P0 live-store blocker is confirmed should theme work proceed, and it must follow the release/rollback SOP: one file, unpublished preview, manual QA, backup, explicit human confirmation, then publish.

## Historical Build Documents

These files are important background from the Build stage, but they are not the daily execution entry point during Monitor Riser Validation.

| File | Use now | Status |
| --- | --- | --- |
| `docs/OBODESK_MVP_SCOPE.md` | Understand evidence-based MVP boundaries and stage criteria. | Historical/current strategy reference. |
| `docs/OBODESK_PROBLEM_EVIDENCE_MAP.md` | Understand target users, scenarios, weak evidence, and validation questions. | Historical/current evidence map. |
| `docs/OBODESK_AGENTIC_WORKFLOW_DESIGN.md` | Understand AI, Shopify, Product Center, Feishu, n8n, TikTok, and human review boundaries. | Historical/current workflow reference. |
| `docs/OBODESK_ADVERSARIAL_REVIEW_LOG.md` | Understand adversarial review and Continue / Modify / Pause decisions. | Historical/current review reference. |
| `docs/OBODESK_AI_NATIVE_STARTUP_METHOD.md` | Understand OboDesk's AI-native startup methodology and stage judgment. | Methodology reference. |
| `docs/OBODESK_MVP5_SAFE_PDP_DRAFT_V0.1.md` | Safe PDP draft for MVP5. | Draft only; do not publish or treat as official facts. |
| `docs/OBODESK_MVP5_PRODUCT_CENTER_SYNC_DRAFT_V0.1.md` | Product Center field sync review draft. | Draft only; do not write formal Product Center records. |

## Product Center And AI Shopping References

Use only when reviewing Product Center or AI-shopping readiness, not as daily Validation execution files.

| File | Purpose | Status |
| --- | --- | --- |
| `docs/PRODUCT_CENTER_V1_SOP.md` | Product Center v1.0 operating model. | Reference. |
| `docs/PRODUCT_CENTER_V1_LOG.md` | Product Center v1.0 closure and status log. | Reference. |
| `docs/PRODUCT_CENTER_STATUS_FLOW.md` | Product Center status fields and transition rules. | Reference. |
| `docs/DAILY_PRODUCT_LAUNCH_SOP.md` | Earlier daily product launch workflow from Shopify to Product Center review. | Reference; not current daily focus. |
| `docs/OBODESK_PRODUCT_FACT_VERIFICATION_FIELD_GUIDE.md` | Field guide for manual product fact verification. | Current guardrail. |
| `docs/AI_SHOPPING_READINESS_FIELDS_V1.md` | P0 fields for AI-friendly PDP planning before metafields. | Planning reference only. |

## Draft / Review Only / Do Not Treat As Source Of Truth

These files are easy to misuse because they look complete, import-ready, or official. They must not be used as current facts without human review.

| File or directory | Misuse risk | Required handling |
| --- | --- | --- |
| `data/obodesk_mvp_product_fact_checklist.csv` | Historical checklist with `TBD` / `Pending` fields. | Historical template only. Do not import, sync, or publish from it. |
| `data/obodesk_ai_pdp_p0_template.csv` | AI PDP P0 draft can contain unverified assumptions or outdated handles. | Content ideation only. Do not treat as facts. |
| `data/obodesk_mvp5_product_center_sync_review_draft.csv` | Looks like a Product Center import file. | Do not import while `Ready_To_Import = No`. |
| `data/obodesk_monitor_riser_14day_validation_log_draft.csv` | Looks like a performance tracker but starts mostly blank. | Record reviewed evidence only. Blank/pending rows are not validation results. |
| `docs/OBODESK_MVP5_SAFE_PDP_DRAFT_V0.1.md` | Looks publishable because copy is polished. | Draft only. Do not publish or convert to metafields. |
| `docs/OBODESK_MVP5_PRODUCT_CENTER_SYNC_DRAFT_V0.1.md` | Looks like a complete sync plan. | Review draft only. Do not write formal records from it. |
| `docs/OBODESK_DESK_MAT_SAFE_SHOPIFY_UPDATE_2026-05-31.md` | Looks like a Shopify Admin update packet. | Manual Shopify Admin packet only; not automation input. |
| `theme/obodesk-theme/README.md` | Still describes Shopify Skeleton Theme, not OboDesk operations. | Theme scaffold reference only. |
| `docs/README.md` | Thin older docs readme. | Prefer this `docs/INDEX.md`. |
| `.codex-lark-*` | Local connector/Codex artifacts. | Tool cache only. Do not use as source of truth. |
| `rollback-backups/` | Contains recovery/audit/preview snapshots. | Do not treat as current theme source unless executing rollback with SOP. |

## Frozen During Validation

The following are frozen during the current Validation stage unless the user explicitly approves a separate task and review path:

- No theme batch push.
- No broad homepage redesign or unrelated storefront build work.
- No Product Center expansion or formal import.
- No Shopify metafield creation from drafts.
- No automation workflow expansion.
- No new plugin installation.
- No SKU matrix expansion.
- No new product category expansion.
- No TikTok/public content publishing before human claim review.
- No use of draft files as official facts.

## Current Manual Validation Loop

1. Confirm cold visitor path is healthy.
2. Publish or manually run a small approved content test.
3. Record traffic source, views, CTR, PDP visits, add-to-cart, checkout, orders, comments, questions, and pain points.
4. Classify evidence as None / Weak / Medium / Strong.
5. Decide Continue / Modify / Pause.
6. Avoid new build work unless a P0 live-store blocker appears.

## Reference Materials

| File | Purpose | Status |
| --- | --- | --- |
| `docs/reference/FOUNDERS_PLAYBOOK_CN_EXTRACT.md` | Source excerpt used for OboDesk AI-native startup method. | Reference only. |
| `references/` | External design/reference materials. | Background only; confirm current product direction before use. |
