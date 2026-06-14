# OboDesk Shopify Cold Visitor Manual Test Checklist Draft

Draft date: 2026-06-12

Status: Local draft only. Manual checklist only. Codex must not modify Shopify, theme, checkout, cart, variant, payment, shipping, product status, or Product Center from this file.

## 1. Test Purpose

Before the 14-day `Signature Monitor Riser` validation starts, a human operator must manually confirm that a cold visitor can move through the live Shopify path:

Home -> Collection -> PDP -> Add to cart -> Cart -> Checkout -> payment entry -> trust pages.

This is a readiness check for small-scale market validation. It is not PMF evidence by itself.

## 2. Required Record Fields

Use these fields for every checklist item:

- Result: Pass / Fail / Need Review.
- Screenshot: file path, URL, or note.
- Issue description.
- Severity: P0 / P1 / P2.
- Suggested action.
- Owner.
- Checked at.

Severity definitions:

- P0: Blocks or invalidates the 14-day validation test.
- P1: Creates trust, clarity, or measurement risk but does not fully block a tiny test.
- P2: Cosmetic, copy, or later polish issue.

## 3. Codex Boundary

Codex can:

- Provide this checklist.
- Help classify manually reported issues.
- Draft safe notes and review summaries.

Codex cannot:

- Log in to Shopify.
- Edit products, PDP, pages, inventory, markets, shipping, payment, or publication status.
- Modify Shopify theme.
- Run `theme push`.
- Modify checkout, cart, variant selector, payment, or product form code.
- Publish content or TikTok posts.
- Write to Feishu Product Center.
- Run automation.

## 4. Manual Test Checklist

| Area | Manual check | Must be human live check? | Codex role | P0 if failed? | P1/P2 if failed? | Result | Screenshot | Issue description | Severity | Suggested action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Home | Open `https://obodesk.com` in a logged-out or incognito browser. | Yes | Checklist only | Site cannot load, wrong domain, broken layout prevents navigation. | Minor copy or visual polish. |  |  |  |  |  |
| Home | Confirm first Featured Essentials / Monitor Riser entry leads to `/products/signature-monitor-riser-live`. | Yes | Checklist only | Monitor Riser entry missing, broken, or goes to wrong product/404. | Link exists but label/copy needs polish. |  |  |  |  |  |
| Home | Confirm no admin preview bar or logged-in-only UI appears for cold visitor. | Yes | Checklist only | Public visitor sees admin/preview UI or blocked page. | None. |  |  |  |  |  |
| Collection | Open Desk Setup or relevant collection from navigation or card. | Yes | Checklist only | Collection does not load or hides Monitor Riser. | Collection copy or order needs polish. |  |  |  |  |  |
| Collection | Confirm Monitor Riser card shows title, price, image, and clickable path. | Yes | Checklist only | Missing product, 404 link, missing image, wrong product. | Image quality or card copy weak. |  |  |  |  |  |
| PDP | Open Monitor Riser PDP directly: `/products/signature-monitor-riser-live`. | Yes | Checklist only | PDP 404, sold out unexpectedly, product title wrong product, page broken. | Copy clarity, image count, or trust detail needs review. |  |  |  |  |  |
| PDP | Confirm title is `Signature Monitor Riser`. | Yes | Checklist only | Wrong title or test product shown. | Title is correct but handle still has `live`; handle cleanup is P2 and must not happen now. |  |  |  |  |  |
| PDP | Confirm price is visible and consistent with current product facts. | Yes | Checklist only | Price missing or inconsistent enough to break trust. | Compare-at pricing unclear. |  |  |  |  |  |
| PDP | Confirm product image loads. | Yes | Checklist only | Main image missing or broken. | More images desirable later. |  |  |  |  |  |
| PDP | Review visible PDP claims for forbidden wording. | Yes | Can classify risk | Health, neck, cervical, medical, ergonomic treatment, universal compatibility, or exact load capacity appears without evidence. | Generic copy is weak but safe. |  |  |  |  |  |
| Add to cart | Click Add to cart. | Yes | Checklist only | Button missing, disabled while product should be sellable, add fails. | Button style/copy polish. |  |  |  |  |  |
| Add to cart | Confirm the correct product and quantity enter cart. | Yes | Checklist only | Wrong product, wrong price, quantity not added. | Cart UX polish. |  |  |  |  |  |
| Cart | Open cart page. | Yes | Checklist only | Cart does not load, product disappears, quantity/price wrong. | Cart visual polish. |  |  |  |  |  |
| Cart | Confirm checkout button is visible and usable. | Yes | Checklist only | Cannot proceed to checkout. | Button placement or copy polish. |  |  |  |  |  |
| Checkout | Proceed to checkout as a cold visitor. | Yes | Checklist only | Checkout cannot be reached. | Checkout branding polish. |  |  |  |  |  |
| Checkout | Confirm shipping/contact form is usable for the intended market. | Yes | Checklist only | Shipping unavailable to intended test market, form blocked, rate unavailable. | Minor copy issue. |  |  |  |  |  |
| Payment entry | Confirm payment entry appears, including PayPal / Venmo / PayPal payment if still configured. | Yes | Checklist only | No usable payment option appears. | Payment label polish. |  |  |  |  |  |
| Footer | Confirm footer is visible and links work. | Yes | Checklist only | Footer missing or key trust links broken. | Footer copy polish. |  |  |  |  |  |
| Shipping | Open Shipping / Shipping and Taxes page. | Yes | Checklist only | 404, blank, contradictory shipping promise. | Copy can be more branded later. |  |  |  |  |  |
| Return | Open Refund / Return policy. | Yes | Checklist only | 404, blank, materially unclear return path. | Formatting polish. |  |  |  |  |  |
| Privacy | Open Privacy Policy. | Yes | Checklist only | 404, blank, wrong policy content. | Formatting polish. |  |  |  |  |  |
| Terms | Open Terms of Service. | Yes | Checklist only | 404, blank, wrong policy content. | Formatting polish. |  |  |  |  |  |
| Contact | Open Contact / Support page and confirm support email is visible. | Yes | Checklist only | No contact path or broken support page. | Support copy can be sharper. |  |  |  |  |  |
| Mobile home | Repeat home and Monitor Riser entry on mobile viewport or real phone. | Yes | Checklist only | Cannot navigate to PDP or layout blocks buying path. | Visual polish. |  |  |  |  |  |
| Mobile PDP | Confirm product image, title, price, Add to cart, and checkout path on mobile. | Yes | Checklist only | Add to cart or checkout blocked on mobile. | Spacing or minor copy issue. |  |  |  |  |  |
| Mobile trust pages | Confirm footer/trust links are reachable on mobile. | Yes | Checklist only | Trust links unreachable or broken. | Formatting polish. |  |  |  |  |  |

## 5. P0 Blockers

Stop the validation launch until fixed if any P0 appears:

- Storefront cannot load for a cold visitor.
- Monitor Riser card or direct PDP URL is broken.
- Monitor Riser PDP shows sold out or no purchasable state when it should be testable.
- Add to cart fails.
- Cart loses product, shows wrong product, or wrong price.
- Checkout cannot be reached.
- No payment entry appears.
- Shipping is unavailable to the intended test region.
- Main image is missing or product appears untrustworthy enough to invalidate the test.
- PDP includes unsupported health, medical, neck, cervical, ergonomic treatment, universal compatibility, or exact load-capacity claims.
- Admin preview UI is visible to public visitors.

## 6. P1 / P2 Items That Can Be Deferred

These should be recorded but should not block the first tiny validation test:

- Handle still contains `live`.
- PDP image count is limited but main image works.
- Footer/policy pages are visually basic but readable.
- Homepage copy could be more persuasive.
- Collection order could be improved.
- More product specs are desirable but not required if unsafe claims are avoided.
- Product Center sync draft remains `Ready_To_Import = No`.

## 7. Manual Test Output Summary Template

- Test date:
- Tester:
- Browser/device:
- Market/location:
- Overall result: Pass / Fail / Need Review.
- P0 blockers:
- P1 issues:
- P2 issues:
- Screenshots/evidence:
- Decision: Ready for tiny validation / Fix P0 first / Need founder review.
- Next action:
