# OboDesk Agentic Workflow Design

Updated: 2026-05-20

Purpose: this document defines the roles, inputs, outputs, review points, and automation boundaries for OboDesk's evidence-based MVP workflow. It is designed to keep AI and tools useful without increasing premature system complexity.

## Workflow Principle

AI and agents should support evidence collection, product fact verification, review preparation, and small controlled execution. They should not replace human judgment for market direction, claims approval, publishing, Product Center formal writes, or automation of unstable workflows.

## Source Of Truth Priority / 事实源优先级

When sources conflict, use this priority order:

1. Shopify commerce facts: product IDs, variant IDs, handles, prices, inventory, publication status, product URLs, order data, and checkout behavior.
2. Supplier or physical evidence: supplier pages, supplier sheets, packaging, product images, certifications, direct supplier confirmation, and physical sample checks.
3. Product Center reviewed records: human-reviewed Feishu/Product Center fields and review statuses.
4. Local review drafts: CSV review drafts, safe PDP drafts, sync drafts, and Codex-generated validation reports.
5. AI draft content: generated summaries, PDP drafts, scripts, hypotheses, and recommendations.

AI drafts and local review drafts are never official facts by themselves. They must be checked against Shopify commerce facts, supplier evidence, and human review before they can influence Product Center formal records or Shopify storefront content.

## Agent And Tool Roles / Agent 与工具角色

| Agent / tool / Agent 或工具 | Role / 角色 | Inputs / 输入 | Outputs / 输出 | Human review point / 人工审核点 |
| --- | --- | --- | --- | --- |
| Codex | Local research, code inspection, documentation, CSV validation, draft generation, risk review. | Repo docs, theme files, local CSVs, user instructions, exported Shopify/Product Center data. | Markdown docs, review notes, validation reports, safe drafts, issue lists. | Before any file becomes source of truth, before any generated content is used externally, before code/theme changes. |
| Shopify Admin / storefront | Commerce source of truth and live buying surface. | Product records, variants, prices, inventory, images, collections, policies, checkout settings. | Product IDs, variant IDs, handles, prices, availability, product URLs, analytics, orders. | Before publishing, title changes, product data changes, pricing changes, shipping changes, and PDP copy changes. |
| Product Center / Feishu Base | Structured product asset hub and review workspace. | Shopify-verified fields, supplier evidence, fact verification data, review decisions. | Product status, content status, SEO status, image status, sync review queues, import logs. | Before formal-table writes, status advancement, content approval, and field-level sync decisions. |
| Feishu Docs / Wiki | Persistent operating context and decision records. | SOPs, review summaries, decision logs, weekly evidence summaries. | Long-lived project memory and review artifacts. | Before treating a document as official operating policy. |
| n8n | Future workflow automation after rules are stable. | Stable Shopify exports/API data, Product Center temporary tables, validation rules. | Scheduled checks, notifications, temporary-table syncs, review queues. | Before enabling any production write or notification that affects operations. |
| TikTok / short-form content system | Market signal generator and content testing surface. | Product facts, safe claims, content hypotheses, target user scenarios. | Videos, comments, click signals, content performance, audience objections. | Before publishing claims, using unverified specs, or interpreting views as demand. |
| Human founder/operator | Orchestrator and final decision owner. | Evidence map, analytics, customer feedback, Product Center status, agent summaries. | Scope decisions, prioritization, approval, pause/pivot decisions. | Always required for product positioning, claims, publishing, automation escalation, and stage changes. |

## Core MVP Workflow

### 1. Product Fact Verification

- Input: Shopify product data, supplier pages, supplier sheets, images, packaging, physical samples.
- Codex output: verification worksheet, missing-field list, claims-to-avoid list, safe draft.
- Human review: confirm facts, mark uncertain fields, approve or reject claim boundaries.
- Current boundary: do not publish draft facts to Shopify or Product Center formal records until reviewed.

### 2. Product Center Draft Review

- Input: verified Shopify identity fields, supplier-backed product facts, safe PDP draft.
- Codex output: Product Center sync review draft and field-level status.
- Human review: decide which fields can enter draft import, which remain `Need Review`, and which are `Do Not Sync`.
- Current boundary: formal Product Center writes require human approval.

### 3. Storefront And PDP Improvement

- Input: approved product facts, observed shopper questions, PDP analytics, support feedback.
- Codex output: proposed copy, theme impact notes, risk review, test checklist.
- Human review: approve scope and claims before Shopify edits.
- Current boundary: do not modify product form, variant selector, cart, checkout, payment, or PDP metafield rendering unless the specific task is approved.

### 4. Market Evidence Collection

- Input: Shopify analytics, order data, support emails, comments, interviews, content performance.
- Codex output: weekly evidence summary, objections list, problem evidence map update proposal.
- Human review: judge whether evidence changes MVP scope.
- Current boundary: do not infer PMF from views, internal progress, or one-off traffic.

### 5. Content Experimentation

- Input: target user hypothesis, safe product facts, content angle, call to action.
- Codex output: scripts, captions, claim risk review, experiment log template.
- Human review: approve content claims and test purpose.
- Current boundary: do not publish unverified technical, health, ergonomic, waterproof, compatibility, or performance claims.

## Forbidden Automation For Current Stage / 禁止自动化的环节

Do not automate these actions yet:

- Shopify product publishing.
- Shopify price, inventory, shipping, or variant changes.
- Shopify metafield creation from draft Product Center fields.
- Shopify PDP content publication from AI drafts.
- Feishu Product Center formal-table overwrites.
- Product status advancement to `Ready for Publish` without human approval.
- Claim approval for health, ergonomic, waterproof, electrical, charging, compatibility, audio, or certification statements.
- Product category expansion based only on AI research.
- TikTok/content publishing without claim review.
- Stage-change decisions from MVP to launch or scale.

## Draft-Only Outputs / 只能作为草稿或审核材料的输出

The following outputs are draft/review artifacts only and cannot directly become official Product Center data, Shopify data, or public storefront content:

- Codex-generated PDP copy.
- AI-generated product summaries, target users, use cases, and benefit statements.
- Product Center sync review drafts.
- CSV verification worksheets before human approval.
- Claims-to-avoid lists before claim owner review.
- TikTok scripts, captions, and hooks before claim review.
- Weekly evidence summaries before founder/operator interpretation.
- n8n-generated alerts or temporary-table data before human review.

Any output that affects product facts, claims, pricing, availability, publication status, customer-facing PDP content, or formal Product Center status must pass human review first.

## Suitable Later Automation / 适合后续自动化的环节

These may become automation candidates after the workflow is manually stable:

- Scheduled Shopify export checks.
- Duplicate Product ID / Variant ID / SKU detection.
- Missing image, missing price, missing inventory, and missing SEO alerts.
- Product Center temporary-table imports.
- Weekly evidence summary drafts from Shopify analytics and support messages.
- Product fact missing-field reminders.
- Claims-to-avoid linting for draft PDP copy.
- Content performance summaries.
- Review queue notifications.

## Minimum Automation Readiness Criteria

Before automating a workflow, all criteria must be true:

- The process has been run manually multiple times.
- Inputs and outputs are stable.
- Error cases are known.
- Escalation paths are clear.
- A human review point exists.
- Automation failure will not create unacceptable customer, product, data, or business risk.
- There is a log or audit trail.

## Current Design Choice

For the current evidence-based MVP stage, the correct workflow is human-reviewed, semi-manual, and evidence-oriented. Agent speed should be used to reduce analysis and preparation cost, not to increase unvalidated operational surface area.
