# AI Shopping Readiness Fields V1

Updated: 2026-05-13

## Purpose

This document defines the Product Center v1.0 P0 fields for AI-friendly product detail pages. These fields are intended to help OboDesk standardize product content before any Shopify metafields or theme rendering changes are created.

Current scope:

- Product Center planning only.
- No Shopify metafields are created in this phase.
- No theme files are changed in this phase.
- Shopify remains the source of truth for commerce facts such as product IDs, handles, variant IDs, pricing, inventory, and publication status.

## Field Rules

- Write for US and European shoppers.
- Use clear, factual English.
- Do not claim medical, ergonomic, health, productivity, or performance benefits that cannot be verified.
- Do not invent technical specifications.
- Use `TBD` when a specification is not confirmed.
- Keep content concise enough for PDP display and AI retrieval.
- Prefer reusable structured lists over long marketing copy.
- Review every field before syncing to Shopify metafields in a later phase.

## P0 Field Definitions

| Field Name | Purpose | Recommended Product Center Type | Filling Rules | Example Content | Sync to Shopify Metafield Later | Suggested Metafield |
| --- | --- | --- | --- | --- | --- | --- |
| PDP_AI_Summary | One concise AI-readable product summary for PDP, search, recommendation, and shopping assistant use. | Long text | 1-2 sentences. Describe what the product is best used for. Avoid unsupported claims. | `A compact monitor riser for users who want a cleaner desk layout, better screen placement, and simple storage space under the display.` | Yes | `obodesk.ai_recommendation_summary` |
| PDP_Target_User | Defines who the product is mainly intended for. | Multi select or JSON text list | Use 3-6 short user groups. Avoid overly broad audiences such as `everyone`. | `home office users; hybrid workers; desk setup builders` | Yes | `obodesk.target_user` |
| PDP_Pain_Point | Defines the shopper problems the product addresses. | Multi select or JSON text list | Use 3-6 practical pain points. Do not imply medical treatment or guaranteed outcomes. | `low monitor position; limited desk storage; visual desktop clutter` | Yes | `obodesk.pain_point` |
| PDP_Best_For | Defines the strongest fit cases. | Multi select or JSON text list | Use 3-6 concise fit statements. Keep them factual and scenario-based. | `single-monitor workstations; compact desk organization; keyboard storage` | Yes | `obodesk.best_for` |
| PDP_Not_For | Defines reasonable non-fit cases to reduce bad recommendations and returns. | Multi select or JSON text list | Use 2-5 honest limitations. Use `TBD` if a limitation depends on unconfirmed specs. | `users needing adjustable height; heavy equipment setups where load capacity is not confirmed` | Yes | `obodesk.not_for` |
| PDP_Use_Cases | Defines shopper scenarios and PDP content blocks. | JSON text list | Use 3-6 use cases. Focus on how the item is used in a desk setup. | `home office desk; laptop and monitor setup; clean workspace upgrade` | Yes | `obodesk.use_cases` |
| PDP_Specs | Defines factual specs for PDP display and future structured data. | JSON text with `label` and `value` pairs | Only include confirmed facts. Mark unconfirmed values as `TBD`. Do not guess dimensions, materials, wattage, ports, or compatibility. | `[{"label":"Material","value":"TBD"},{"label":"Dimensions","value":"TBD"}]` | Yes | `obodesk.specs` |

## Suggested JSON Formats

For list fields, Product Center may store semicolon-separated text during manual operation, but the future Shopify metafield value should be normalized as a JSON array.

Example:

```json
["home office users", "hybrid workers", "desk setup builders"]
```

For `PDP_Specs`, use a JSON array of label/value objects:

```json
[
  {
    "label": "Material",
    "value": "TBD"
  },
  {
    "label": "Dimensions",
    "value": "TBD"
  }
]
```

## Review Status

Recommended Product Center status field:

| Field Name | Recommended Type | Values |
| --- | --- | --- |
| PDP_Content_Status | Single select | `Draft`, `Need Review`, `Approved`, `Needs Shopify Fact Check`, `Do Not Sync` |

Use `Draft` for first-pass examples. Move to `Approved` only after product facts are checked against Shopify and product sourcing records.
