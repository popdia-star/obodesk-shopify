# Daily Product Launch SOP

Updated: 2026-05-08

## Purpose

This SOP defines the daily product launch workflow for OboDesk after Product Center v1.0.

The core principle is Shopify-first, Feishu-standardized:

- Shopify creates and stores real product facts.
- Feishu standardizes, enriches, reviews, and manages product assets.
- Codex prepares clean local files and validation reports.
- Human review remains required before formal Feishu updates.

## Daily Workflow

1. Select products from 1688.
2. Create real products in Shopify through the current product import workflow.
3. Organize products in Shopify as Draft or Active.
4. Export Shopify product data.
5. Import exported data into a Feishu temporary table.
6. Validate required Shopify fields.
7. Clean and normalize product records locally with Codex.
8. Generate Product Center import files and validation reports.
9. Manually review Excel / CSV outputs.
10. Merge clean data into Product Center v1.0.
11. Update Import_Log.
12. Move products through lifecycle status until published or archived.

## Required Validation Fields

Before clean data is merged into Product Center v1.0, validate:

- Product ID
- Handle
- Variant ID
- SKU
- Vendor
- Product Type
- Tags
- Price
- Image URL
- Published Status
- SEO fields

## Product Status Workflow

Use clear status values to track product lifecycle:

- Draft
- Need Review
- Need Content
- Ready for Shopify
- Published
- Archive

For the full Product Center status design, see `docs/PRODUCT_CENTER_STATUS_FLOW.md`.

Recommended Product Center workflow fields:

- Workflow_Status
- Content_Status
- SEO_Status
- Image_Status
- TikTok_Status
- Shopify_Sync_Status
- Human_Approved
- Error_Note
- Last_Checked_At

Recommended `Workflow_Status` values:

- Draft
- Need Review
- Need Content
- Need SEO
- Need Image
- Ready for Shopify
- Ready for Publish
- Published
- Archive
- Error

Daily status rules:

- New imported products start as `Draft`.
- Products with missing `Product_ID` or `Handle` should be marked `Error`.
- Products missing `Description_HTML` should be marked `Need Content`.
- Products missing `SEO_Title` or `SEO_Description` should be marked `Need SEO`.
- Products missing `Image_URL` should be marked `Need Image`.
- Products with content, SEO, and images completed can move to `Ready for Shopify`.
- Products manually approved can move to `Ready for Publish`.
- Products published in Shopify can move to `Published`.
- Products not aligned with OboDesk can move to `Archive`.

## Why Shopify-First

Shopify is the preferred first step because it provides real commerce data:

- Real Product IDs
- Real Variant IDs
- Real Handles
- Real image URLs
- Real prices
- Real publication status

Feishu should not be used to invent product data from scratch. It should standardize, enrich, review, and manage Shopify-based product assets.

This makes future Codex, n8n, and AI-agent automation more reliable because automation can depend on real Shopify identifiers and validated product facts.

## Automation Direction

Use Product Center as the structured source for:

- SEO generation
- Product description generation
- TikTok script generation
- Image checklist generation
- Publish-readiness checks

Keep Shopify sync semi-automatic first. Avoid full automation until validation rules are stable, especially for:

- Duplicate Product IDs
- Duplicate Variant IDs
- Missing SKU values
- Missing inventory
- Missing image URLs
- Incomplete SEO fields
- Draft versus published status

Feishu internal automation should come first. n8n should be added later for scheduled checks, notifications, and Shopify sync after workflow statuses are stable.

Do not overwrite formal Product Center data directly. Use temporary import tables first, validate data, then merge clean records into the formal table.

## Current Pause

Third-batch product expansion is paused until the current daily workflow is stable.

The next operating priority is to make the Product Center workflow repeatable before expanding product volume.
