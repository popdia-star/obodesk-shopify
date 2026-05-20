# OboDesk Data Directory README

Updated: 2026-05-20

Purpose: this directory contains local CSV worksheets, review drafts, and early content drafts for OboDesk's evidence-based MVP stage. These files are not automatically approved for Product Center import, Shopify metafield sync, or storefront publication.

This README defines the usage boundaries for all CSV files in `data/` to prevent accidental import, sync, or publication.

## Source Of Truth Priority

When sources conflict, use this priority order:

1. Shopify commerce facts: product IDs, variant IDs, handles, prices, inventory, publication status, product URLs, order data, checkout behavior.
2. Supplier / physical evidence: supplier pages, supplier sheets, packaging, product images, certifications, direct supplier confirmation, physical samples.
3. Product Center reviewed records: human-reviewed Feishu / Product Center fields and review statuses.
4. Local review drafts: CSV review drafts, safe PDP drafts, sync drafts, Codex validation reports.
5. AI draft content: generated summaries, PDP drafts, scripts, hypotheses, recommendations.

CSV files in this directory are local review materials unless a human explicitly promotes them through the current Product Center workflow.

## Global Rules

- Product Center writes require human confirmation before import.
- Shopify publishing, product edits, metafield creation, and PDP publication require human confirmation.
- PDP copy usage requires human confirmation.
- Files with `Ready_To_Import = No` must not be imported.
- Files with `draft`, `review`, `p0`, or `checklist` in the filename are not formal source-of-truth files by default.
- AI-generated fields must be checked against Shopify commerce facts and supplier / physical evidence before use.
- Do not use any CSV here as storefront content unless the relevant fields have been reviewed and approved.

## CSV Status Overview

| CSV file | Current status | Allowed use | Forbidden use |
| --- | --- | --- | --- |
| `data/obodesk_mvp_product_fact_verification_today.csv` | Manual verification only. Partially verified product facts worksheet. | Manual product fact review, missing-field tracking, claim-risk review. | Do not import directly into Product Center. Do not sync directly to Shopify metafields. Do not use directly as PDP official copy. |
| `data/obodesk_mvp5_product_center_sync_review_draft.csv` | Review draft only. Product Center pre-import review CSV. | Field-level human review before any Product Center draft import decision. | Do not import while `Ready_To_Import = No`. Do not write formal Product Center records. Do not sync to Shopify metafields. |
| `data/obodesk_mvp_product_fact_checklist.csv` | Historical checklist / early verification template. | Reference old checklist structure or compare early assumptions. | Do not use as current source of truth. Do not import. Do not sync. Do not publish from it. |
| `data/obodesk_ai_pdp_p0_template.csv` | AI PDP P0 draft. First-pass content planning only. | Early content planning, field ideation, AI shopping readiness discussion. | Do not treat as verified facts. Do not import into Product Center. Do not sync to Shopify metafields. Do not use as final PDP copy. |

## File Notes

### `data/obodesk_mvp_product_fact_verification_today.csv`

Status: manual verification only.

This file contains Shopify-checked fields and supplier-evidence additions for MVP products, but it remains a working verification worksheet. Some fields are still marked `Need Manual Review`, `Missing Evidence`, `Unclear`, or `Partially Verified`.

Allowed:

- Manual fact review.
- Missing-field identification.
- Risky-claim detection.
- Preparing human review notes.

Forbidden:

- Direct Product Center import.
- Direct Shopify metafield sync.
- Direct storefront PDP rendering.
- Treating `Partially Verified` as fully approved.

### `data/obodesk_mvp5_product_center_sync_review_draft.csv`

Status: review draft only.

This file is a Product Center sync review draft for the MVP5 product set. It is intended to help decide which fields may later be imported after human review.

Important boundary:

- `Ready_To_Import = No` means the file must not be imported.
- `Product_Center_Write_Status = Review Draft Only` means it is not formal Product Center data.

Allowed:

- Manual review before a future draft import.
- Identifying `Ready`, `Need Review`, and `Do Not Sync` fields.
- Comparing safe facts with risk-control notes.

Forbidden:

- Formal Product Center import.
- Shopify metafield sync.
- PDP publication.
- Any automated write into Feishu / Product Center.

### `data/obodesk_mvp_product_fact_checklist.csv`

Status: historical checklist / early verification template.

This file appears to be an earlier checklist with many `TBD` or `Pending` fields. It can help understand the original verification plan, but it should not override newer verification and review files.

Allowed:

- Historical reference.
- Checklist structure reference.

Forbidden:

- Current product fact source.
- Product Center import.
- Shopify metafield sync.
- PDP official copy source.

### `data/obodesk_ai_pdp_p0_template.csv`

Status: AI PDP P0 draft.

This file contains first-pass AI-friendly PDP fields. It is useful for content planning but may contain unverified assumptions, draft positioning, or outdated handles.

Allowed:

- Content planning.
- PDP field ideation.
- AI shopping readiness discussion.

Forbidden:

- Treating content as verified facts.
- Product Center import.
- Shopify metafield sync.
- Final PDP copy publication.

## Human Review Checklist Before Any Data Promotion

Before any CSV-derived field is promoted into Product Center, Shopify metafields, PDP copy, or published content, confirm:

- The Shopify handle, Product ID, Variant ID, price, inventory, and publication status match Shopify Admin.
- Product specs are backed by supplier / physical evidence.
- Missing or uncertain fields remain `Need Review`, `Missing Evidence`, or `Do Not Sync`.
- Risky claims are removed or explicitly approved.
- The target field has a named human reviewer.
- The target import or publication path is documented.
- The CSV no longer has `Ready_To_Import = No` for the rows being considered.

## Current Default Rule

All CSV files in `data/` are review materials by default. They are not formal Product Center data, not Shopify metafield sources, and not PDP publication sources unless a human explicitly approves a later promotion step.
