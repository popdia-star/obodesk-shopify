# Product Center Status Flow

Updated: 2026-05-08

## Purpose

This document defines the recommended workflow status fields and daily usage rules for OboDesk Product Center v1.0 in Feishu.

Current operating constraints:

- Product Center v1.0 is the official product data hub in Feishu.
- Shopify is the source of truth for real Product IDs, Variant IDs, Handles, prices, image URLs, and publication status.
- The Feishu Agent is not used for the official workflow.
- n8n will be added later only after workflow statuses and validation rules are stable.
- Current implementation is documentation-only.

## Recommended Fields

Add or standardize the following fields in Product Center:

| Field | Type | Purpose |
| --- | --- | --- |
| Workflow_Status | Single select | Main product workflow state. |
| Content_Status | Single select | Tracks product description and content readiness. |
| SEO_Status | Single select | Tracks SEO title, description, and metadata readiness. |
| Image_Status | Single select | Tracks main image, image URLs, alt text, and checklist readiness. |
| TikTok_Status | Single select | Tracks short-form video planning or script readiness. |
| Shopify_Sync_Status | Single select | Tracks Shopify data sync quality and freshness. |
| Human_Approved | Checkbox | Confirms manual approval before publish or formal workflow advancement. |
| Error_Note | Long text | Records missing data, validation failures, or manual correction notes. |
| Last_Checked_At | Date/time | Records the latest manual or automated validation time. |

## Workflow_Status Values

Recommended values:

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

## Status Transition Rules

Use the following rules as the baseline operating logic:

- New imported products start as `Draft`.
- Products with missing `Product_ID` or `Handle` should be marked `Error`.
- Products missing `Description_HTML` should be marked `Need Content`.
- Products missing `SEO_Title` or `SEO_Description` should be marked `Need SEO`.
- Products missing `Image_URL` should be marked `Need Image`.
- Products with content, SEO, and images completed can move to `Ready for Shopify`.
- Products manually approved can move to `Ready for Publish`.
- Products published in Shopify can move to `Published`.
- Products not aligned with OboDesk can move to `Archive`.

## Daily Operating Rules

- Do not overwrite formal Product Center data directly.
- Use temporary import tables first.
- Validate data before merging into the formal Product Center table.
- Keep Shopify as the source of truth for real commerce fields.
- Human approval is required before publishing.
- Keep `Error_Note` specific and actionable.
- Update `Last_Checked_At` after each manual check or automated validation pass.
- Do not move records to `Ready for Publish` unless `Human_Approved` is checked.

## Suggested Status Field Details

### Content_Status

Recommended values:

- Missing
- Drafted
- Need Review
- Approved

### SEO_Status

Recommended values:

- Missing
- Drafted
- Need Review
- Approved

### Image_Status

Recommended values:

- Missing Image
- Pending Alt Review
- Need Checklist
- Approved

### TikTok_Status

Recommended values:

- Not Started
- Script Drafted
- Need Review
- Approved

### Shopify_Sync_Status

Recommended values:

- Not Synced
- Synced
- Needs Shopify Fix
- Needs Product Center Fix
- Error

## Automation Direction

Automation should be phased:

1. Feishu internal automation first.
   - Use Feishu views, filters, reminders, and simple field rules to surface missing data.
   - Keep formal table changes human-reviewed.

2. n8n later.
   - Use n8n for scheduled checks, notifications, and Shopify sync once the status rules are stable.
   - Use n8n to write into temporary tables or review queues before touching formal data.

3. Avoid full automation until validation rules are stable.
   - Do not fully automate publish decisions.
   - Do not fully automate formal Product Center overwrites.
   - Do not let agents update official records without validation and human approval.

## Acceptance Criteria

This status flow is ready to use when:

- Product Center has the recommended status fields.
- Daily operators understand the transition rules.
- Temporary import tables are used before formal table merges.
- Shopify remains the source of truth.
- Human approval is required before publishing.
- Error records are visible through QA views.
