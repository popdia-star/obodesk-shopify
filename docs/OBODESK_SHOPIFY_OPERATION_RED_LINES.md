# OboDesk Shopify Operation Red Lines

## 1. Purpose

This document defines the non-negotiable Shopify operation red lines for OboDesk during the Validation stage.

The purpose is to prevent accidental live theme overwrite, homepage/navigation/footer changes, PageFly conflicts, incorrect CSV imports, and unsafe Product Center synchronization.

Current phase: Validation  
Current primary validation object: Signature Monitor Riser  
Repository: `obodesk-shopify`

## 2. Highest-Level Red Lines

The following actions are prohibited unless separately reviewed and explicitly approved:

1. Do not run full theme push.
2. Do not publish from `rollback-backups/`.
3. Do not use the local theme as the full truth of the online Live Theme.
4. Do not overwrite the online Live Theme with local files.
5. Do not import any CSV where `Ready_To_Import = No`.
6. Do not modify Shopify products, variants, inventory, navigation, PageFly pages, homepage, footer, checkout, payment, logistics, or policies without human confirmation.
7. Do not publish or deploy before confirming the current Published Theme name and Theme ID.
8. Do not treat Validation preparation materials as market evidence.

## 3. High-Risk Files That Must Not Be Synced Directly

The following files are high-risk and must not be pushed or overwritten directly without file-level review, current live comparison, and rollback plan:

- `config/settings_data.json`
- `templates/*.json`
- `sections/*-group.json`
- `sections/page.liquid`
- `snippets/pagefly-main-js.liquid`
- `locales/en.default*.json`

Reason:

These files may affect homepage layout, navigation, footer, collection pages, product pages, PageFly integration, theme editor settings, and storefront text.

## 4. Required Checks Before Any Shopify Theme Operation

Before any Shopify theme operation, the operator must confirm:

1. Current Published Theme name.
2. Current Published Theme ID.
3. Whether the operation target is Live Theme or Preview Theme.
4. Whether the URL contains `preview_theme_id`.
5. Whether PageFly is active on the target page.
6. Whether Theme Editor preview and real storefront are showing the same target.
7. Whether desktop and mobile screenshots have been saved.
8. Whether a rollback path exists.
9. Whether the change is single-file or batch.
10. Whether the change is necessary for the current Validation stage.

If any item is unknown, the operation must stop.

## 5. Safe Operation Types

The following operations are generally allowed during Validation if they remain read-only or documentation-only:

- Read-only architecture audit.
- File listing.
- Single-file diff review.
- Git status review.
- Documentation updates under `docs/`.
- Manual screenshot verification.
- Manual product fact review.
- Manual evidence logging.
- Drafting SOPs, audit reports, and work logs.

## 6. Prohibited Operation Types During Validation

The following operations are prohibited during the current Validation stage unless separately approved:

- Batch theme push.
- Theme publish.
- Theme deploy.
- Theme pull that overwrites local source.
- Direct publish from backup folders.
- Product CSV import.
- Product Center automatic synchronization.
- Metafield creation or update.
- Automatic inventory update.
- Automatic navigation update.
- Automatic homepage update.
- Automatic PageFly update.
- Automatic collection or PDP update.
- Any operation that changes payment, checkout, logistics, policies, or tax settings.

## 7. Product Data Red Lines

Current product data and CSV files are review materials unless explicitly approved.

Do not import:

- MVP5 review CSV.
- Product Center sync review draft CSV.
- Any CSV where `Ready_To_Import = No`.
- Any file whose source version is unclear.
- Any file not confirmed against the current Shopify product state.

Monitor Riser must not enter public claim testing until these facts are manually confirmed:

- Material.
- Load capacity.
- Net weight.
- Package contents.
- Origin/country of manufacture.
- Supplier evidence screenshots or links.
- Current Shopify product status.
- Current inventory policy.

## 8. Validation Evidence Red Lines

During Validation:

1. Planned content is not evidence.
2. Draft CSV rows are not evidence.
3. Supplier claims are not market evidence.
4. AI-generated copy is not evidence.
5. Storefront screenshots are QA evidence, not demand evidence.
6. Real evidence must come from traceable traffic, PDP behavior, ATC, checkout, orders, messages, comments, emails, or user quotes.

## 9. Stop Conditions

Stop immediately if:

- The target Theme ID is unclear.
- The target page is controlled by PageFly but PageFly state is unknown.
- The command would affect more than one file.
- The operation would touch `settings_data.json`.
- The operation would touch templates or section groups.
- The operation would import product data.
- The operation would update live navigation, homepage, footer, PDP, collection, checkout, payment, shipping, or policy settings.
- The operator cannot explain the rollback path.

## 10. Current Default Rule

For OboDesk Validation stage, the default rule is:

Documentation first.  
Manual verification second.  
Single-file changes only after approval.  
No full sync.  
No automatic import.  
No live publish without human confirmation.
