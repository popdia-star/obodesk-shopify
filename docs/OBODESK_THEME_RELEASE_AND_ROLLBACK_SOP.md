# OboDesk Theme Release And Rollback SOP

## 1. Scope

This SOP applies to OboDesk Shopify theme work involving theme file edits, preview theme uploads, Live Theme publishing, and emergency rollback.

It does not authorize changes to Shopify Pages, products, inventory, publication status, Handles, Redirects, Markets, Shipping profiles, Metafields, or Feishu data.

## 2. Pre-Release Checklist

- Confirm the exact user-approved change scope.
- Confirm the target store and target theme.
- Confirm the working directory is a valid Shopify theme directory.
- Confirm Git status and identify unrelated local changes.
- Run `theme check` before any upload.
- Duplicate the current Live Theme before any publish.
- Create an unpublished preview theme before any publish.
- Upload only one changed theme file at a time.
- Complete manual QA after every upload.
- Record all commands, files, Theme IDs, and QA results.

## 3. Store And Theme ID Verification

Before any theme operation, verify:

- Store domain.
- Current Live Theme name.
- Current Live Theme ID.
- Target preview theme name.
- Target preview theme ID.

For OboDesk production, the known store is:

- `obo-5.myshopify.com`

Never infer the target store or Theme ID from memory alone.

## 4. Working Directory Verification

Before running any Shopify theme command, confirm the command is running inside the intended theme directory.

Default rule:

- Do not run `theme push` outside a valid theme directory.
- If Shopify CLI prints `It doesn't seem like you're running this command in a theme directory.`, stop immediately.
- Any warning during directory verification is a stop condition.

## 5. Git Status Check

Before editing or uploading, run:

```bash
git status --short
```

Record:

- Files already modified before the task.
- Files modified by the current task.
- Any unrelated local changes that must not be touched.

Do not use Git status as proof that the online Shopify theme matches local files.

## 6. Theme Check

Run `theme check` before uploading any theme file.

Required result:

- No offenses for the intended upload scope.

If `theme check` fails, stop and fix locally before any upload.

## 7. Remote Live Theme Duplicate Backup

Before publishing any recovery or release theme, duplicate the current Live Theme.

Record:

- Backup theme name.
- Backup Theme ID.
- Backup status.
- Time created.

Do not publish until the remote Live Theme backup exists and is recorded.

## 8. Unpublished Preview Theme Creation

Before publishing, create or update an unpublished preview theme.

Record:

- Preview theme name.
- Preview Theme ID.
- Source commit or source file state.
- Uploaded file list.

Manual preview approval is required before publish.

## 9. Single-File Modify And Upload

Default rules:

- Direct batch `theme push` to the Live Theme is forbidden by default.
- Uploading multiple files at once is forbidden by default.
- Modify only one theme file at a time.
- Upload only one theme file at a time.
- Run manual QA immediately after each upload.

Any exception requires explicit human approval before execution.

## 10. Manual QA

After each upload, manually verify:

- Target page loads.
- Intended change is visible.
- Header, footer, homepage, PDP, cart, and checkout-critical flows are not unexpectedly changed.
- Mobile and desktop views are acceptable when relevant.

Record the QA result before continuing.

## 11. Pre-Publish Human Confirmation

Before publishing any theme, obtain explicit human confirmation that:

- The preview theme was reviewed.
- The preview result is approved.
- The Live Theme duplicate backup exists.
- The exact theme to publish is identified by name and Theme ID.

Unreviewed themes must not be published.

## 12. Post-Publish Manual QA

After publish, manually verify the live storefront.

Record:

- Live URL checked.
- Pages checked.
- Time checked.
- Result.
- Any unexpected changes.

## 13. Required Log Fields

Each release or recovery log must include:

- Store domain.
- Live Theme name and Theme ID before work.
- Backup theme name and Theme ID.
- Preview theme name and Theme ID.
- Published theme name and Theme ID.
- Git commit or file source.
- Files modified.
- Files uploaded.
- Commands executed.
- Warnings or errors.
- Manual QA result.
- Final live verification result.

## 14. Immediate Stop Conditions

Stop immediately if any of the following occurs:

- Shopify CLI prints any warning.
- Shopify CLI says the command is not running in a theme directory.
- Store domain or Theme ID cannot be verified.
- Git status shows unexpected changes in files needed for the operation.
- `theme check` fails.
- More files than expected are queued for upload.
- Manual QA fails or is incomplete.
- The Live Theme backup has not been created before publish.
- The unpublished preview has not been reviewed before publish.

## 15. Emergency Rollback Flow

Use this sequence for emergency recovery:

1. Stop all write operations.
2. Verify the correct store and current Live Theme in read-only mode.
3. Duplicate the current Live Theme for evidence and rollback safety.
4. Create an isolated local recovery directory.
5. Create or upload an unpublished recovery preview theme.
6. Restore only the required known-good files.
7. Run `theme check`.
8. Manually preview the recovery theme.
9. Publish only the confirmed recovery theme.
10. Manually QA the live storefront.
11. Record all Theme IDs, files, commands, and QA results.

Preferred rollback pattern:

`duplicate current Live Theme -> create unpublished recovery preview -> manual preview -> publish confirmed recovery theme`

## 16. Forbidden Actions

- Do not directly batch `theme push` to the Live Theme by default.
- Do not upload multiple files at once by default.
- Do not run `theme push` outside a valid theme directory.
- Do not continue after any warning.
- Do not publish before manual QA is complete.
- Do not publish without a remote Live Theme duplicate backup.
- Do not publish without an unpublished preview theme.
- Do not change Shopify Pages, products, inventory, publication status, Handles, Redirects, Markets, Shipping profiles, Metafields, or Feishu data unless a separate task explicitly approves that scope.
