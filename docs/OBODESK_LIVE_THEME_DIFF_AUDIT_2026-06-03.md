# OboDesk Live Theme Difference Audit — 2026-06-03

## 1. Audit Scope

- Live Theme:
  `OboDesk Recovery Preview 662f7f6`
  Theme ID: `155001913484`
  Status: `live`

- Local formal theme directory:
  `theme/obodesk-theme`

- Audit directory:
  `rollback-backups/live-theme-audit-155001913484`

## 2. Summary

- Online file count: 52
- Local formal theme file count: 62
- Matching file count: 44
- Difference file count: 19

Batch `theme push` must remain frozen.

## 3. P0 — 禁止直接同步文件

- `config/settings_data.json`
  - Shopify online configuration file.
  - Direct push is forbidden.

- `sections/footer-group.json`
  - Footer online structure and menu configuration are different.
  - Overwrite is forbidden.

- `sections/page.liquid`
  - Online version contains About, FAQ, and B2B special page logic.
  - Local version is a generic template.
  - Overwrite is forbidden.

- `snippets/pagefly-main-js.liquid`
  - Exists online but is missing locally.
  - PageFly or online-generated snippet.
  - Must be preserved and must not be deleted.

- `templates/*.json`
  - Direct sync is forbidden by default.

- `sections/*-group.json`
  - Direct sync is forbidden by default.

## 4. P1 — 需人工复核文件

- `locales/en.default.json`
- `locales/en.default.schema.json`
- `sections/header.liquid`

`sections/header.liquid`:

- Local version removes the Kits navigation link.
- It can be treated as a future single-file preview release candidate.
- It must follow:
  `unpublished preview -> manual QA -> duplicate current Live Theme -> publish -> post-publish manual QA`

## 5. Safe / Ignore

- `sections/obodesk-hero.liquid`
  - Line-ending-only difference.
  - No business difference.
  - Do not upload.

- `config/settings_data.json`
  - Although the observed difference is line-ending-only, direct upload remains forbidden.

- Local project metadata files:
  - Not theme release targets.
  - Do not upload as theme files.

## 6. Files Already Matching Live Theme

- `sections/featured-products.liquid`
- `sections/footer.liquid`
- `sections/obodesk-core-system.liquid`
- `sections/obodesk-kits.liquid`
- `sections/obodesk-lighting.liquid`
- `sections/obodesk-why.liquid`
- `layout/theme.liquid`
- `templates/index.json`
- `sections/header-group.json`

## 7. Release Policy

- Batch `theme push` remains frozen.
- Uploading the full local theme directory is forbidden.
- Uploading `config/settings_data.json` is forbidden by default.
- Uploading `templates/*.json` is forbidden by default.
- Uploading `sections/*-group.json` is forbidden by default.
- Overwriting PageFly-related snippets is forbidden by default.
- Only one file may be modified and uploaded at a time.
- Stop immediately when any warning appears.
- Every release must first create an unpublished preview.
- Every release must complete manual QA before publish.
- Before every publish, duplicate the current Live Theme for backup.
- After every publish, complete manual QA again.

## 8. Next Allowed Candidate

- `sections/header.liquid`
- Target: hide the Kits navigation entry.
- Status: allowed to enter the single-file preview release process, but not yet executed.
