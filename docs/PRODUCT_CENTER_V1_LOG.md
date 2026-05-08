# Product Center v1.0 Log

Updated: 2026-05-08

## Current Status

Product Center v1.0 is now the official product data hub for OboDesk.

The current operating model is Shopify-first:

- Shopify product data is created first through the current product import workflow.
- Shopify remains the source of truth for real sales data.
- Feishu Product Center receives Shopify-based data for structured asset management.
- The Feishu formal table is now the long-term product master table.
- Third-batch product expansion is paused until the current workflow is stable.

## System Roles

Shopify is responsible for real commerce facts:

- Product IDs
- Variant IDs
- Handles
- Product URLs
- Image URLs
- Prices
- Inventory
- Vendor
- Product type
- Tags
- Published status

Feishu Product Center is responsible for standardized product asset management:

- SPU and SKU structure
- Product review status
- Content and SEO planning
- Image checklist
- Video and short-form content planning
- Publish-readiness tracking
- Archive and lifecycle management

Codex is responsible for local processing:

- Cleaning Shopify exports
- Generating import files
- Validating required fields
- Producing merge reports
- Preparing files for manual Feishu import

## Completed v1.0 Setup

- Product Center v1.0 has been created in Feishu.
- MVP5 baseline product data has been imported.
- CoreBatch2 Lighting data has been merged.
- The Feishu formal table displays correctly.
- Product Center v1.0 SOP has been documented.
- The workflow is moving from setup into daily operations.

## Operating Boundary

- Do not use Feishu to invent product data from scratch.
- Do not write directly to the Feishu formal table through API automation yet.
- Do not fully automate Shopify sync until validation rules are stable.
- Pause third-batch product expansion until the daily workflow is repeatable.

## Next Direction

Product Center should become the source for:

- SEO generation
- Product description generation
- TikTok script generation
- Image checklist generation
- Publish-readiness checks
- Product fix and cleanup tasks

Shopify sync should remain semi-automatic first. Full automation should wait until field validation, duplicate handling, and manual review rules are stable.
