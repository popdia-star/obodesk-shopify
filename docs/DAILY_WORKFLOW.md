# OboDesk Shopify Theme 日常工作流

## 项目名称

OboDesk Shopify Theme

## 当前 live theme 状态

当前主题处于 V1 搭建后的收尾检查阶段。首页、Collection 页面、Product 页面、Cart 页面已经完成基础版本，Header 导航已回退为 5 个 collection 导航。

首页和购物车中的 All Products 链接已完成修复，并已提交、推送到 live theme。正式站 `obodesk.com` 已验证生效。

正式站产品购买闭环已验证通过：Product → Add to cart → Cart → Checkout 可以跑通，Checkout 页面显示 PayPal / Venmo / PayPal payment 支付入口正常。

产品图片缺失问题已确认是 Shopify 后台产品数据问题，不是 theme 图片渲染问题。Shopify 后台已给 `Test Desk Product` 上传产品图，Collection / Product / Cart / Checkout 商品图均已正常展示。

Product 页面已完成可售状态体验优化：`product.liquid` 增加 `current_variant.available` 判断，可售时显示 Add to cart 和 Buy it now，不可售时显示 Sold out disabled。最新提交为 `32ff019 add product availability button state`，已推送到 live theme。

当前 Git 状态：`git status --short` 干净。

## 今天已完成

1. 修复 `docs/DAILY_WORKFLOW.md` 编码问题，并提交。

2. 修复首页与购物车中的 All Products 链接：
   - Hero Explore essentials → Desk Setup collection
   - Featured Essentials 产品卡片 → Desk Setup / Lighting collection
   - Explore all essentials CTA → Desk Setup collection
   - Empty cart Explore essentials → Desk Setup collection
   - 已提交并推送到 live theme
   - 正式站 `obodesk.com` 已验证生效

3. 验证购买闭环：
   - Product → Add to cart → Cart → Checkout 已跑通
   - Checkout 显示 PayPal / Venmo / PayPal payment 入口正常

4. 修复产品图片数据问题：
   - Shopify 后台已给 `Test Desk Product` 上传产品图
   - Collection / Product / Cart / Checkout 商品图均已正常展示
   - 确认不是 theme 图片渲染问题

5. 优化 Product 页面可售状态：
   - `product.liquid` 增加 `current_variant.available` 判断
   - 可售时显示 Add to cart 和 Buy it now
   - 不可售时显示 Sold out disabled
   - 已提交：`add product availability button state`
   - 已推送到 live theme

6. 当前 Git 状态：
   - `git status --short` 干净
   - 最新提交：`32ff019 add product availability button state`

## 已完成事项

- 首页 V1
- Collection 页面 V1
- Product 页面 V1
- Cart 页面 V1
- Header 导航已回退为 5 个 collection 导航
- 首页和购物车 All Products 链接修复
- 购买闭环验证
- 产品图片缺失问题排查和后台数据修复
- Product 页面 available / Sold out / disabled 状态优化

## 明天建议任务计划

1. 正式站最终人工复测：
   - 首页导航
   - 首页 CTA
   - Collection 页面
   - Product 页面
   - Cart 页面
   - Checkout 页面

2. 清理测试数据：
   - 决定是否隐藏或删除 `Test Desk Product`
   - 将 Signature Monitor Riser 作为真实主产品
   - 检查产品标题、价格、描述、图片是否符合 OboDesk V1 定位

3. 首页内容清理：
   - Featured Essentials 是否继续用静态卡片，还是改为真实产品 / collection
   - 检查 Hero 文案是否需要从 `Build Your Desk Environment` 升级为 `Orchestrate Your Flow`

4. 店铺基础页面检查：
   - Contact
   - Shipping
   - Refund policy
   - Privacy policy
   - Terms of service

5. V1 发布前检查清单：
   - 移动端显示
   - 商品库存
   - 支付入口
   - 域名正式访问
   - Footer 信息
   - 是否仍有 Powered by Shopify

6. 明天原则：
   - 先只读检查，不要直接改 theme
   - 每次只改一个小范围
   - 每轮修改后 theme check
   - 修改后本地预览验证
   - 确认后提交并推送 live theme

## 当前待办事项

- 正式站最终人工复测
- 清理测试产品和测试数据
- 确认真实主产品内容
- 检查店铺基础页面和政策页面
- V1 发布前移动端、库存、支付、域名、Footer 信息检查

## Git 工作流

1. 修改前先检查工作区状态：

   ```powershell
   git status
   ```

2. 每轮改动后运行 Shopify Theme Check：

   ```powershell
   cd D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify\theme\obodesk-theme
   shopify theme check
   ```

3. 确认改动内容：

   ```powershell
   cd D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify
   git diff
   git status
   ```

4. 确认后再提交：

   ```powershell
   git add docs/DAILY_WORKFLOW.md
   git commit -m "update daily workflow docs"
   ```

## 2026-04-28 Product salability investigation

- Old `Signature Monitor Riser` showed `Sold out` on the live storefront.
- Sidekick and Liquid debug showed an inconsistency in product salability state.
- Direct `/cart/add` tests confirmed old `signature-monitor-riser` and `signature-monitor-riser-v2` were not purchasable.
- Final replacement used the verified purchasable `Test Desk Product` configuration to create a new product:
  - `/products/signature-monitor-riser-live`
- New `Signature Monitor Riser Live` now displays `Add to cart` / `Buy it now` correctly.
- Price is correct at `$89.00`.
- Product image displays correctly.
- Old `signature-monitor-riser` and `signature-monitor-riser-v2` have been set to `Draft`.
- `signature-monitor-riser-live` has been added to the `Desk Setup` collection.
- Conclusion: this round was mainly caused by abnormal Shopify product data / inventory configuration, not theme code.
- Follow-up: confirm whether Home `Featured Essentials` should link directly to `/products/signature-monitor-riser-live`.

## 2026-04-28 收尾记录

已完成：
1. 排查 Signature Monitor Riser 售罄问题。
2. 确认旧产品 /products/signature-monitor-riser 前台显示 Sold out，且直接 /cart/add 测试不可购买。
3. 新建的 /products/signature-monitor-riser-v2 也不可购买，因此不再继续修复旧坏产品。
4. 最终使用已验证可购买的 Test Desk Product 配置，复制/创建出新的正式主产品：
   - /products/signature-monitor-riser-live
5. 新主产品 Signature Monitor Riser Live 已验证：
   - 产品页正常打开
   - 产品图正常显示
   - 价格 $89.00 正常
   - Add to cart 正常显示
   - Buy it now 正常显示
6. 旧产品处理：
   - /products/signature-monitor-riser 已设置为 Draft
   - /products/signature-monitor-riser-v2 已设置为 Draft
7. Collection 处理：
   - signature-monitor-riser-live 已加入 Desk Setup collection
8. 首页 Featured Essentials 处理：
   - 第一张 Signature Monitor Riser 卡片已从 Desk Setup collection 链接改为直接链接：
     /products/signature-monitor-riser-live
9. 代码提交与上线：
   - 提交：cca7fcf link featured riser card to live product
   - 已推送到 live theme：OboDesk V1 Local Build #153947996300
10. 当前状态：
   - git status 干净
   - 主产品入口、产品页、加购链路已恢复正常

今天建议任务：
1. 正式站复测首页 Featured Essentials → Signature Monitor Riser 是否直达 /products/signature-monitor-riser-live。
2. 复测新主产品 Add to cart → Cart → Checkout。
3. 检查 Desk Setup collection 是否只展示可购买主产品和必要测试产品。
4. 决定是否隐藏 Test Desk Product。
5. 检查首页其他 3 张 Featured Essentials 卡片是否继续保留静态占位，还是改为真实产品。
6. 检查 footer / policy / contact / shipping 页面。
7. 今天原则：先复测和内容清理，不要大改 theme。

## 2026-04-29 产品清理记录

- Test Desk Product 已设置为 Draft，不再显示在 Online Store storefront。
- Test Desk Product 未删除，保留为可恢复测试产品。
- Signature Monitor Riser Live 保持 Active，并发布到 Online Store。
- Desk Setup collection 已确认只展示正式主产品 Signature Monitor Riser。
- 正式主产品价格 $89.00，产品图正常显示。
- 当前 Collection 清理已完成。

## 2026-04-29 Footer 配置记录

- Footer menu handle 为 footer。
- 原因：live theme footer section 的 menu 为空，导致正式站底部不显示导航链接。
- 已将 footer-group.json 中 Footer section 的 menu 绑定为 footer。
- theme check 通过。
- 已推送到 live theme。
- 正式站底部已显示 Footer 链接：
  Search / Privacy Policy / Terms of Service / Shipping & Taxes / Refund Policy / Contact Us / Your Privacy Choices / About Us / FAQ
- 后续待办：逐个检查核心 Footer 页面内容是否完整。

## 2026-04-29 Footer 与基础页面检查记录

- Footer menu 已成功显示在正式站底部。
- Footer links 已出现：Search / Privacy Policy / Terms of Service / Shipping & Taxes / Refund Policy / Contact Us / Your Privacy Choices / About Us / FAQ。
- 已检查核心页面不是 404：
  - Refund Policy 可打开
  - Shipping & Taxes 可打开
  - Privacy Policy 可打开
  - Terms of Service 可打开
  - Contact Us 可打开
- 当前问题：
  - Footer 页面整体排版较简陋
  - Contact Us 页面内容明显不足，目前基本只有标题
  - Policy 页面内容可读但偏基础，后续需要品牌化和英文版优化
  - Powered by Shopify 仍显示，后续决定是否移除
- 结论：
  - Footer 链接功能已打通
  - 下一步优先优化 Contact Us 页面内容，其次再优化 Policy 页面视觉和品牌文案

## 2026-04-29 Contact Us 页面更新记录

- Contact Us 页面此前内容过少，基本只有标题。
- 已通过 Shopify 后台更新 Contact Us 页面正文。
- 页面 URL 保持为 /pages/contact。
- 页面已包含：
  - 订单和桌面搭建咨询说明
  - 客服邮箱 support@obodesk.com
  - 响应时间 1-2 business days
  - 订单问题所需信息
  - 退换货和保修问题所需信息
  - Business & Bulk Orders 联系说明
- 正式站 /pages/contact 已验证内容正常显示。
- 当前仍待优化：页面视觉排版较基础，后续可统一优化 page 模板样式。

## 2026-04-29 About Us / FAQ 页面检查记录

- About Us 页面已检查，可正常打开。
- About Us 页面当前有 Our Story / Our Mission / What We Offer / Our Promise 内容。
- FAQ 页面已检查，可正常打开。
- FAQ 页面当前包含 Shipping / Returns & Refunds / Products / Orders & Payments 等内容。
- 两个页面都不是 404，也不是空页。
- 当前判断：内容可用，但文案偏通用，后续可品牌化优化。
- 更主要的问题是基础 page 模板整体排版较简陋，包括页面宽度、段落间距、标题层级和 footer 对齐。
- 下一步建议：不要继续逐页手动补内容，改为统一优化 page 模板样式。

## 2026-04-29 信任页基础整理收尾记录

已完成：
- Footer menu 已在正式站底部正常显示。
- 普通 page 页面样式已优化并上线。
- Contact Us 页面已补充英文客服内容。
- Privacy Policy 页面已修正：原本误放了 Returns and Warranty 内容，已替换为正确英文隐私政策。
- Shipping and Taxes 页面已替换为英文内容，并完成基础富文本排版。
- Refund Policy / Returns and Warranty 页面已更新英文内容。
- Support 页面已替换为英文客服支持内容。
- 客服邮箱已统一为 obosupport@gmail.com。
- Shopify Sidekick 已替换旧邮箱 support@obodesk.com 为 obosupport@gmail.com。
- support@obo-ai.com 未在页面中发现。
- 已更新并确认涉及页面：
  - Contact Us
  - Privacy Policy
  - Shipping and Taxes
  - Returns and Warranty / Refund Policy
  - Support
  - Business Purchasing Program
- 所有相关页面仍保持 published。
- 本轮 Shopify 后台页面内容修改未改 theme code。

已验证：
- /pages/contact 可打开，内容和样式正常。
- /pages/support 可打开，邮箱已显示 obosupport@gmail.com。
- /pages/shipping-and-taxes 可打开，英文内容已显示。
- Footer 中核心链接可打开，不是 404。
- 底部出现的 Shopify preview/admin bar 属于管理员预览状态，普通访客不可见，不是网站 bug。

当前遗留：
- Support 页面富文本层级仍可继续优化：部分小标题建议设置为 Heading，退换货信息建议设置为 bullet list。
- Policy / Support / FAQ 等页面内容后续还可以继续品牌化、法务化和视觉细节优化。
- Powered by Shopify 是否移除待决定。
- 下一阶段建议：检查 checkout / footer / policy 页面在无痕访客视图下的最终表现。

## 2026-04-29 无痕访客视图最终复测记录

- 使用无痕窗口访问 obodesk.com。
- 确认没有 Shopify preview/admin bar。
- 首页 Featured Essentials 第一张 Signature Monitor Riser 可进入正式商品页。
- 商品页 Add to cart / Buy it now 正常。
- Cart 页面产品、价格、数量显示正常。
- Checkout 可进入支付页。
- Footer 核心链接均可打开，不是 404。
- Contact / Privacy Policy / Shipping and Taxes / Refund Policy / Support / About Us / FAQ 页面可正常打开。
- 客服邮箱统一显示为 obosupport@gmail.com。
- 当前信任页基础整理和访客路径复测通过。

## 2026-04-29 Footer V1 品牌化优化记录

- 已完成 OboDesk Footer V1 品牌化优化。
- 已推送到 live theme。
- 修改文件：
  - theme/obodesk-theme/sections/footer.liquid
  - theme/obodesk-theme/assets/critical.css
- Footer 从默认链接平铺升级为品牌收口区 + Navigation + 底部版权/支付图标。
- 已移除 Powered by Shopify。
- 已显示 OboDesk 品牌说明。
- 已显示客服邮箱 obosupport@gmail.com。
- 已显示响应时间 Usually replies within 1-2 business days。
- 保留现有 footer menu 动态链接。
- 保留 payment icons。
- 本地预览和正式站验证通过。
- 整体符合克制、专业、系统感的 footer 气质。
- 当前 V1 暂不升级为 Shop by System / Support / Company 三列，避免过度复杂化。

## 2026-05-01 Featured Essentials read-only check

- Checked the four Home Featured Essentials cards.
- The current Featured Essentials area is a hardcoded section, not a dynamic product list.
- The first card, `Signature Monitor Riser`, already links to the verified purchasable product:
  - `/products/signature-monitor-riser-live`
- `Essential Desk Mat` is currently a static placeholder card and links to the Desk Setup collection:
  - `/collections/desk-setup`
- `Screen Sync Light` is currently a static placeholder card and links to the Lighting collection:
  - `/collections/lighting`
- `Monitor Light Bar` is currently a static placeholder card and links to the Lighting collection:
  - `/collections/lighting`
- Current card imagery is CSS-drawn visual treatment, not Shopify product images.
- The last three cards have not yet been confirmed as real Shopify products.
- Do not hard-link the last three cards to product URLs until those products exist and are purchasable, to avoid 404 or non-purchasable product experiences.
- Low-risk strategy: keep the last three cards linking to collections, then replace them with product links after real products are created.
- Today, avoid a larger homepage structure change and keep the current overall design stable.

## 2026-05-01 Featured Essentials and Wool Felt Desk Mat checkout fix

- Completed the Featured Essentials second-card real product link upgrade.
- `Signature Monitor Riser` remains linked to `/products/signature-monitor-riser-live`.
- `Essential Desk Mat` was updated to `Essential Wool Desk Mat`.
- The second card link was updated to `/products/obodesk-premium-wool-felt-desk-mat`.
- Investigated the Wool Felt Desk Mat initial Sold out / cart add failure issue.
- Confirmed the root cause was not theme code and not inventory; the `guangdong` fulfillment location was not included in the general shipping profile delivery zones.
- Added the `guangdong` fulfillment location to the Shopify Shipping general profile and reused the US / Canada / Europe delivery zones.
- Did not add a China delivery zone.
- China market is set to Draft / inactive.
- Fixed `product.liquid` multi-variant button state handling.
- Wool Felt Desk Mat Medium / Large / Extra Large can all be added to cart.
- Cart and Checkout validation passed.
- Verified the live storefront Home Featured Essentials second-card entry.
- Today's result: Featured Essentials was upgraded from 1 real purchasable product entry to 2 real purchasable product entries.

## 2026-05-01 Featured Essentials third product entry upgrade

- Completed the Featured Essentials third-card real product link upgrade.
- The PC Sync LED product was cleaned into the formal product name: `PC RGB Sync Light Strip`.
- The product handle remains `pc-sync-rgb-monitor-light-strip`.
- The product has been published to Online Store.
- The product has been added to the Lighting collection.
- Vendor was changed to `OboDesk`.
- Product Type was set to `Lighting`.
- The product has been configured as a physical product and added to the general shipping profile.
- The third card, `Screen Sync Light`, now links to `/products/pc-sync-rgb-monitor-light-strip`.
- Live storefront verification passed: product page, Add to cart, Cart, and Checkout all work.
- Today's result: Featured Essentials was upgraded from 2 real purchasable product entries to 3 real purchasable product entries.
- The fourth card, `Monitor Light Bar`, temporarily remains linked to `/collections/lighting` until the real product is ready.

## 2026-05-02 Featured Essentials fourth product entry upgrade

- Completed the Featured Essentials fourth-card real product link upgrade.
- RGB Monitor Light Bar product cleanup and validation are complete.
- Product URL is `/products/rgb-monitor-light-bar`.
- Product has been published to Online Store.
- Product has been added to the Lighting collection.
- Vendor is `OboDesk`.
- Product Type is `Lighting`.
- Both valid variants require shipping.
- Both valid variants have been added to the general shipping profile.
- Both valid variants have `guangdong` inventory and are `availableForSale`.
- The fourth card, `Monitor Light Bar`, now links to `/products/rgb-monitor-light-bar`.
- Live storefront verification passed: product page, Add to cart, Cart, and Checkout all work.
- Today's result: all four Featured Essentials cards now complete the real purchasable product entry loop.
- Current four entries:
  1. `Signature Monitor Riser` -> `/products/signature-monitor-riser-live`
  2. `Essential Wool Desk Mat` -> `/products/obodesk-premium-wool-felt-desk-mat`
  3. `Screen Sync Light` -> `/products/pc-sync-rgb-monitor-light-strip`
  4. `Monitor Light Bar` -> `/products/rgb-monitor-light-bar`

## 2026-05-02 Power collection initial fill

- Completed the initial Power collection fill.
- Power collection URL is `/collections/power`.
- Added `8 Port USB C Hub` to the Power collection.
- Added `8-Outlet Rack Mount PDU` to the Power collection.
- Both products are `ACTIVE`.
- Both products have been published to Online Store.
- Power collection currently has 2 products, so the storefront collection is no longer empty.
- Live storefront verification passed: Power collection page opens and both products are visible.
- Tested that USB-C Hub and PDU can be added to Cart.
- Checkout can be entered.
- No theme code was modified in this round.
- Follow-up optimization: Power product titles, images, descriptions, PDU B2B/Pro expression, and storefront display order.

## 2026-05-03 Desk Infrastructure collection initial fill

- Completed the initial Desk Infrastructure collection fill.
- Desk Infrastructure collection URL is `/collections/desk-infrastructure`.
- Added 5 core desk system products:
  1. `Signature Monitor Riser`
  2. `OboDesk Premium Wool Felt Desk Mat`
  3. `PC RGB Sync Light Strip`
  4. `RGB Monitor Light Bar`
  5. `8 Port USB-C Hub`
- Did not add PDU, Fiber, SFP, Thermal, ESD, Cat6, Arduino, phone case, screen protector, or other PRO/Data Center or legacy 3C products.
- Current Desk Infrastructure positioning: OboDesk professional desk system collection across Structure / Surface / Lighting / Connectivity.
- Live storefront verification passed: `/collections/desk-infrastructure` opens correctly, 5 products are visible, and each can enter its product page.
- This round only changed Shopify admin collection membership; no theme code was modified.
- Current main navigation status:
  - Desk Setup has products.
  - Lighting has products.
  - Power has products.
  - Desk Infrastructure has products.
  - Kits is still pending.
- Next plan: plan the Kits collection to avoid an empty entry, while gradually cleaning Power and Desk Infrastructure product titles, images, and descriptions.

## 2026-05-03 Kits navigation temporary optimization

- Completed the temporary Kits navigation entry optimization.
- Kits collection currently exists but has 0 products, so `/collections/kits` is not directly exposed as an empty collection page for now.
- Header `Kits` link was changed from the collection URL to `/#obodesk-kits`.
- Clicking Header `Kits` now jumps to the Home Curated Setup Kits area.
- Hero `View setup kits` and Header `Kits` currently point to the same Home solution area.
- No real bundle or kit products were created in this round.
- Current strategy: keep Kits as a future solution entry until real sets such as `Starter Desk Kit`, `Lighting Upgrade Kit`, and `Creator Desk Kit` are created.
- Live storefront verification passed: clicking `Kits` jumps correctly to the Home Kits section.

## 2026-05-03 Main navigation strategic entry baseline closure

- Completed the baseline closure for the 5 strategic main navigation entries.
- Current main navigation remains a minimal first-level navigation:
  - Desk Setup
  - Lighting
  - Power
  - Desk Infrastructure
  - Kits
- Do not restore the old Mega Menu, and do not expose legacy 3C / Data Center mixed-category navigation.
- Power collection has been filled with 2 products:
  1. `8 Port USB C Hub`
  2. `8-Outlet Rack Mount PDU`
- Power collection live storefront verification passed: page opens, products are visible, products can be added to Cart, and Checkout can be entered.
- Desk Infrastructure collection has been filled with 5 core desk system products:
  1. `Signature Monitor Riser`
  2. `OboDesk Premium Wool Felt Desk Mat`
  3. `PC RGB Sync Light Strip`
  4. `RGB Monitor Light Bar`
  5. `8 Port USB-C Hub`
- Desk Infrastructure live storefront verification passed: page opens, 5 products are visible, and each can enter its product page.
- Kits collection is still empty, so `/collections/kits` is not directly exposed.
- Header `Kits` link has been changed to `/#obodesk-kits`.
- Clicking Header `Kits` jumps to the Home Curated Setup Kits area.
- Current strategy: keep Kits as a future solution entry, then create real `Starter Desk Kit`, `Lighting Upgrade Kit`, and `Creator Desk Kit` products later.
- Today's result: all main navigation entries now avoid empty-page experiences.
- Next plan: enter the storefront product quality cleanup stage, starting with Power and Desk Infrastructure products that have overly long titles, supply-chain-looking images, or inconsistent copy.

## 2026-05-03 Main navigation 5-entry baseline closure confirmed

- Completed the baseline closure for the 5 strategic main navigation entries.
- Current main navigation remains a minimal first-level navigation:
  - Desk Setup
  - Lighting
  - Power
  - Desk Infrastructure
  - Kits
- Do not restore the old Mega Menu, and do not expose legacy 3C / Data Center mixed-category navigation.
- Power collection has been filled with 2 products:
  1. `8 Port USB C Hub`
  2. `8-Outlet Rack Mount PDU`
- Power collection live storefront verification passed: page opens, products are visible, products can be added to Cart, and Checkout can be entered.
- Desk Infrastructure collection has been filled with 5 core desk system products:
  1. `Signature Monitor Riser`
  2. `OboDesk Premium Wool Felt Desk Mat`
  3. `PC RGB Sync Light Strip`
  4. `RGB Monitor Light Bar`
  5. `8 Port USB-C Hub`
- Desk Infrastructure live storefront verification passed: page opens, 5 products are visible, and each can enter its product page.
- Kits collection is currently empty, so `/collections/kits` is not directly exposed.
- Header `Kits` link has been changed to `/#obodesk-kits`.
- Clicking Header `Kits` jumps to the Home Curated Setup Kits area.
- Today's result: all main navigation entries now avoid empty-page experiences.
- Next stage: enter the storefront product quality cleanup stage, starting with Power and Desk Infrastructure products that have overly long titles, supply-chain-looking images, or inconsistent copy.

## 2026-05-03 Product page Compare-at price display fix

- Completed the product page Compare-at price display fix.
- Only changed `theme/obodesk-theme/sections/product.liquid`.
- The original product page only displayed `product.price` and did not display `compare_at_price`.
- The price display now uses `selected_or_first_available_variant`.
- When `compare_at_price > price`, the product page displays the Compare-at price as a strikethrough.
- When there is no Compare-at price, the product page only displays the current price.
- USB-C Hub currently displays `$39.99` as the strikethrough price and `$29.99` as the current price.
- Did not modify Add to cart, payment button, variant select, CSS, collection, cart, header, or footer.
- This fix supports promotional price display for all future products that have Compare-at price configured.

## 2026-05-03 Storefront product quality cleanup started

- Entered the storefront product quality cleanup stage.
- Completed the first product cleanup: `OboDesk 8-in-1 USB-C Hub`.
- USB-C Hub title, price, description, variant name, and collection membership have been cleaned.
- USB-C Hub current price is `$29.99`, with Compare-at price set to `$39.99`.
- Fixed the product page Compare-at price display logic.
- Only changed `theme/obodesk-theme/sections/product.liquid`.
- Product pages now support strikethrough Compare-at price display when `compare_at_price > price`.
- Verified that the USB-C Hub product page displays `$39.99` as the strikethrough price and `$29.99` as the current price.
- Completed the second product cleanup: `RGB Monitor Light Bar`.
- RGB Monitor Light Bar title remains concise and unchanged.
- Cleaned the variant names.
- Rewrote the English branded product description.
- Added RGB Monitor Light Bar to the Lighting collection and kept it in Desk Infrastructure.
- Price and Compare-at price remain unchanged.
- Verified that the RGB Monitor Light Bar product page, variants, Add to cart, and Checkout work correctly.
- Follow-up optimization: dynamic price sync when switching variants can be handled as a separate task; image alt text, SKU, and SEO can enter the second product optimization round.

## 2026-05-03 PC RGB Sync Light Strip storefront cleanup

- Completed the third high-exposure storefront product cleanup: `PC RGB Sync Light Strip`.
- Product title remains unchanged: `PC RGB Sync Light Strip`.
- Handle remains unchanged: `pc-sync-rgb-monitor-light-strip`.
- Cleaned 4 variant names:
  1. `24" Monitor — 95cm`
  2. `27" Monitor — 1.1m`
  3. `32"–34" Monitor — 1.3m`
  4. `42" Monitor — 2m`
- Updated price and Compare-at price:
  1. `$24.99` / `$34.99`
  2. `$27.99` / `$37.99`
  3. `$31.99` / `$42.99`
  4. `$35.99` / `$47.99`
- Rewrote the English branded product description.
- Removed Chinese text, wholesale carton specs, `usemap`, `offer-template-0`, and supplier HTML remnants from the description.
- Added the product to the Lighting collection.
- Kept the product in the Desk Infrastructure collection.
- Product remains `ACTIVE` and published to Online Store.
- No theme code was modified in this round.
- Follow-up optimization: Chinese SKU text, image alt text, SEO title/description, and image order can enter the second product optimization round.

## 2026-05-03 Premium Wool Felt Desk Mat storefront cleanup

- Completed the fourth high-exposure storefront product cleanup: `Premium Wool Felt Desk Mat`.
- Product title was optimized from `OboDesk Premium Wool Felt Desk Mat - Dark Grey` to `Premium Wool Felt Desk Mat`.
- Handle remains unchanged: `obodesk-premium-wool-felt-desk-mat`.
- Variant names remain unchanged:
  1. `Medium (80cm x 40cm)`
  2. `Large (90cm x 45cm)`
  3. `Extra Large (100cm x 50cm)`
- Updated price and Compare-at price:
  1. Medium: `$34.99` / `$44.99`
  2. Large: `$39.99` / `$49.99`
  3. Extra Large: `$44.99` / `$54.99`
- Rewrote and strengthened the English branded product description.
- Description now includes Variant Guide and Support information.
- Kept the product in core collections including All Workspace Essentials, Desk & Workspace Setup, and Desk Infrastructure.
- Product remains `ACTIVE` and published to Online Store.
- No theme code was modified in this round.
- Follow-up optimization: image copyright/source confirmation, image alt text, and SEO title/description can enter the second product optimization round.

## 2026-05-03 Signature Monitor Riser storefront cleanup

- Completed the fifth high-exposure storefront product cleanup: `Signature Monitor Riser`.
- Product title remains unchanged: `Signature Monitor Riser`.
- Handle temporarily remains unchanged: `signature-monitor-riser-live`.
- Vendor has been standardized to `OboDesk`.
- Product Type has been set to `Monitor Riser`.
- SKU has been set to `OBODESK-RISER-SIG`.
- Price remains `$89.00`.
- Compare-at price has been set to `$109.00`.
- Rewrote the English branded product description, including Why It Belongs on Your Desk / Designed for Modern Workstations / Setup Ideas / Specifications / Support.
- Added tags: `desk-setup`, `monitor-riser`, `desk-infrastructure`, `workspace`, `productivity`, `structure-layer`.
- Added or confirmed core collections: Desk Infrastructure, All Workspace Essentials, and Desk & Workspace Setup.
- Product remains `ACTIVE` and published to Online Store.
- `availableForSale` remains `true`.
- Add to cart and Checkout verification passed.
- No theme code was modified in this round.
- Follow-up optimization: handle can be cleaned from `signature-monitor-riser-live` to `signature-monitor-riser`, but redirects must be handled separately; product images need 4-6 high-quality additions; SEO title/description can enter the second optimization round.

## 2026-05-03 Sprint 1 closing summary

- Sprint 1 has been cleanly closed.
- Current stage has moved from page buildout and entry repair to storefront product quality cleanup.
- Completed the baseline closure for 5 main navigation entries:
  - Desk Setup
  - Lighting
  - Power
  - Desk Infrastructure
  - Kits
- All 4 Featured Essentials core products now complete the real product entry loop:
  1. `Signature Monitor Riser`
  2. `Premium Wool Felt Desk Mat`
  3. `PC RGB Sync Light Strip`
  4. `RGB Monitor Light Bar`
- Completed the first-round refinement for 5 high-exposure storefront products:
  1. `Signature Monitor Riser`
  2. `Premium Wool Felt Desk Mat`
  3. `PC RGB Sync Light Strip`
  4. `RGB Monitor Light Bar`
  5. `OboDesk 8-in-1 USB-C Hub`
- Fixed the product page Compare-at price display logic.
- Verified core product Add to cart / Cart / Checkout flows.
- Clarified the new storefront collection strategy: actively maintain Desk Setup / Lighting / Power / Desk Infrastructure / Kits as the core line.
- Legacy collections such as All Workspace Essentials and Desk & Workspace Setup are not actively maintained as the new main storefront line.
- Confirmed that legacy 3C products, phone cases, screen protectors, Chinese titles, abnormal inventory products, and Data Center / PRO products should not be mixed into the main storefront for now.
- Confirmed separate follow-up tasks:
  1. Signature Monitor Riser handle cleanup
  2. Signature Monitor Riser image additions
  3. Product image alt text
  4. SKU cleanup
  5. SEO title / description
  6. Dynamic price sync when switching variants
  7. Real Kits bundle product planning
- Next stage, Sprint 2: second-batch product cleanup and collection depth improvement.

## 2026-05-03 Sprint 2.2 Desk Infrastructure collection copy completion

- Sprint 2.2 has been completed.
- Updated the Desk Infrastructure collection description in Shopify Admin.
- New collection description:
  "The structural layer of the OboDesk system: monitor elevation, surface control, lighting, and connectivity essentials selected to create a cleaner, more capable workstation."
- Verified the live collection page:
  - `https://obodesk.com/collections/desk-infrastructure`
- Collection title remains `Desk Infrastructure`.
- Products remain visible.
- Page layout looks normal.
- No theme code changes were required.

## 2026-05-03 Sprint 2.3 Currency and Shopify Markets QA completion

- Sprint 2.3 has been completed.
- Completed Currency / Shopify Markets QA and fallback market cleanup.
- Confirmed store currency remains USD.
- Confirmed US / Canada market remains active.
- Confirmed UK market remains active.
- Confirmed EU market remains active.
- Confirmed the currency issue was caused by Shopify Markets / localization settings, not theme price rendering.
- Updated Backup Region from Austria (`AT`) to United States (`US`).
- Expected behavior after the fix:
  - US and unmatched fallback visitors see USD.
  - EU visitors may still see EUR / local currency.
  - UK visitors see GBP.
- No theme code changes were required.

## 2026-05-06 OboDesk Homepage Hero 双端优化与 Product Center v1.0 准备

### 一、Homepage Hero 完成事项

1. Desktop Hero 已替换为新版 OboDesk 桌面系统图：
   - `theme/obodesk-theme/assets/obodesk-hero-workspace-050605.jpg`
2. Mobile Hero 已新增专用图：
   - `theme/obodesk-theme/assets/obodesk-hero-mobile-0506.jpg`
3. Hero section 已支持 desktop / mobile 图片切换：
   - Desktop 使用 `obodesk-hero-workspace-050605.jpg`
   - Mobile 使用 `obodesk-hero-mobile-0506.jpg`
4. 修复 desktop Hero 图片容器未填满圆角卡片问题。
   - 修改文件：`theme/obodesk-theme/assets/critical.css`
5. 保持标题、副标题、CTA、导航、产品、collection、footer 不变。

### 二、验证结果

1. `shopify theme check` 通过：
   - `45 files inspected with no offenses found`
2. Shopify Live Theme 推送成功：
   - Theme：`OboDesk V1 Local Build`
   - Theme ID：`153947996300`
3. 线上验证：
   - Desktop Hero 显示正常
   - Mobile Hero 显示正常
   - CTA 跳转正常

### 三、Git 提交记录

1. `aa40663` `update homepage hero image and layout`
2. `0e91b5f` `add mobile hero image`
3. `2e90657` `fix hero image container fill`

### 四、GitHub 合并记录

1. 分支：`sprint-2-homepage-optimization`
2. PR：`#1 Sprint 2 homepage optimization`
3. 已合并到 `master`
4. 本地 `master` 已同步
5. `git status` clean

### 五、Product Center 进展

1. 已检查 `OboDesk_Product_Center_v1_Template_PlanA(1).xlsx`
2. `Products_SPU`、`SKU_Variants`、`Product_Images` 字段结构基本通过
3. Shopify 同步字段已具备 v1.0 基础
4. 下一步只处理 5 个 Live Core MVP 产品的 Shopify 同步数据写入和校验

### 六、今日下一步

继续 Product Center v1.0：

1. 只处理 5 个 Live Core MVP 产品
2. 写入 / 校验 `Shopify_Product_ID`
3. 写入 / 校验 `Shopify_Variant_ID`
4. 写入 / 校验 `Shopify_Price`、`Inventory`、`Published`
5. 不处理旧产品、不处理 PRO、不处理 Legacy、不处理 SEO

## 2026-05-07 Product Center v1.0 收尾记录

### 一、今日完成事项

1. Product Center v1.0 正式表已在飞书中显示正常。
   当前正式数据规模：
   - Products_SPU：7 个产品
   - SKU_Variants：13 个 Variant
   - Product_Images：7 条主图记录

2. 已完成 MVP5 Baseline 数据：
   - 5 个产品
   - 7 个 Variant
   - 5 条主图记录

3. 已完成 CoreBatch2 Lighting 数据：
   - 2 个 Lighting 产品
   - 6 个 Variant
   - 2 条主图记录

4. 已完成 CoreBatch2 本地文件生成与修复：
   - 修复 6 个 Variant 的 Shopify_Inventory_Qty
   - Shopify_Inventory_Qty 全部为 50
   - 校验通过
   - 飞书导入准备状态 PASS

5. 已完成 Product Center v1.0 本地正式表合并。
   输出文件：
   - `OboDesk_Product_Center_v1_Merged_20260507.xlsx`
   - `Products_SPU_v1_Merged_20260507.csv`
   - `SKU_Variants_v1_Merged_20260507.csv`
   - `Product_Images_v1_Merged_20260507.csv`
   - `Product_Center_v1_Merge_Report_20260507.md`

   合并结果：
   - Products_SPU：5 + 2 = 7，PASS
   - SKU_Variants：7 + 6 = 13，PASS
   - Product_Images：5 + 2 = 7，PASS
   - 重复 Shopify_Product_ID：无
   - 重复 Shopify_Variant_ID：无
   - 重复 SKU_ID：无
   - 空价格：无
   - 空库存：无

6. 已确认正式表在飞书中显示正常。

7. 已新增 Product Center v1.0 SOP 文档：
   - `docs/PRODUCT_CENTER_V1_SOP.md`

8. 已更新日常工作日志：
   - `docs/DAILY_WORKFLOW.md`

9. 已完成 Git 提交并推送 GitHub：
   - commit hash：`448a570`
   - commit message：`document product center v1 sop`
   - branch：`master`
   - remote：`origin/master`

### 二、今日关键结论

Product Center v1.0 已经从模板阶段进入运营化阶段。

当前系统定位：
- Shopify 是真实销售数据源
- 飞书是标准化产品资产中枢
- Codex 负责本地清洗、校验、合并文件
- 人工负责最终检查和导入飞书
- 暂不使用飞书 API 直接写正式表

### 三、下一步计划

下一阶段暂不扩展第三批产品，先做运营化配置：

1. 在飞书中创建 Import_Log 表。
2. 录入两条历史导入记录：
   - `IMP-20260507-MVP5`
   - `IMP-20260507-BATCH2-LIGHTING`

3. 建立基础 QA 视图。
   Products_SPU：
   - Live Core MVP
   - Missing Shopify ID
   - Missing Image

   SKU_Variants：
   - Missing Variant ID
   - Missing Price
   - Missing Inventory

4. 后续再处理：
   - Chinese Shopify SKU 视图
   - Empty Shopify Real SKU 视图
   - Needs SEO 视图
   - SKU 标准化修复清单
   - 第三批产品筛选

### 四、今日收尾状态

Product Center v1.0 已完成正式表搭建、第二批合并、飞书显示验证、SOP 固化、GitHub 保存。

## 2026-05-08 Product Center v1.0 setup phase closure

- Product Center v1.0 is now treated as the official OboDesk product data hub.
- Shopify remains the source of truth for real product data, including Product IDs, Variant IDs, handles, image URLs, prices, inventory, and publication status.
- Feishu Product Center is used as the standardized product asset hub and long-term product master table.
- The daily workflow is now Shopify-first: create or import products in Shopify, export Shopify data, validate the data, then import clean records into Feishu for structured management.
- Third-batch product expansion is paused until the daily workflow is stable.
- Added `docs/PRODUCT_CENTER_V1_LOG.md` to record the v1.0 closure status and operating boundary.
- Added `docs/DAILY_PRODUCT_LAUNCH_SOP.md` to document the daily product launch workflow, validation fields, lifecycle status, and automation direction.
- No Shopify theme files were changed.
- No product data was modified.
- No Feishu API calls were made.

## 2026-05-13 AI Shopping Readiness v0.1 data modeling

- Completed the PDP theme structure diagnosis for AI-friendly product detail page readiness.
- Confirmed that the current `sections/product.liquid` purchase flow is stable.
- Confirmed that the current phase should not modify the product form, variant selector, Add to Cart, Buy it now, cart, or checkout-related code.
- Designed the AI Shopping Readiness P0 field system for Product Center-first PDP content preparation.
- Added `docs/AI_SHOPPING_READINESS_FIELDS_V1.md` to define the P0 field purpose, filling rules, Product Center field guidance, and future Shopify metafield mapping.
- Added `data/obodesk_ai_pdp_p0_template.csv` with first-pass Draft AI PDP content for 5 MVP products.
- Added `data/obodesk_mvp_product_fact_checklist.csv` for manual verification of true product facts before Product Center import or Shopify metafield planning.
- The 5 MVP products' AI PDP content remains Draft and must not be imported into Product Center, synced to Shopify metafields, or shown on the storefront yet.
- All true product parameters still require manual verification.
- Next step: complete the fact checklist using Shopify Admin, 1688 source products, supplier sheets, physical samples, product images, and packaging information.
- No Shopify theme files were changed.
- No Shopify API calls were made.
- No Shopify metafields were created.
- No Shopify push was performed.
- No Git commit was made.

## 2026-05-14 AI Shopping Readiness v0.1 product fact verification

- Generated and updated `data/obodesk_mvp_product_fact_verification_today.csv` as the current product fact verification worksheet.
- Added `docs/OBODESK_PRODUCT_FACT_VERIFICATION_FIELD_GUIDE.md` to document the bilingual verification fields, source rules, and no-guessing boundaries.
- Shopify Assistant completed read-only Shopify Admin verification for the 5 MVP products.
- Shopify-confirmed backend fields were written into the CSV worksheet, including handles, product IDs, variant IDs, SKUs, product types, vendors, prices, inventory settings, publication status, tags, collections, and main image URLs.
- Completed `Signature Monitor Riser` sample row v0.1:
  - Live sellable size confirmed: `1000 x 260 x 122 mm`.
  - Live sellable color confirmed: `Walnut Brown`.
  - Health and medical risky claims were removed.
  - `Verification_Status` is now `Partially Verified`.
  - `Confidence_Level` is now `Medium`.
  - Remaining manual fields: material evidence, load capacity, package contents evidence, and source screenshot archive.
- Fixed the CSV column alignment issue and confirmed the worksheet has 41 header columns and 41 columns for each of the 5 product rows.
- No Shopify theme files were changed.
- No Shopify data was modified.
- No Shopify metafields were created.
- No Product Center import was performed.
- No Git commit was made.

Next recommended step:

- Continue manual verification with `Premium Wool Felt Desk Mat`.
- Use the `Signature Monitor Riser` sample row as the operating pattern for supplier-backed facts.
- Keep the current boundary: do not guess product parameters, do not import Product Center data, and do not create Shopify metafields until fact verification is complete.

### Hui OS Note / 今日认知沉淀

Theme: OboDesk AI Shopping Readiness v0.1 — Product Fact Verification sample row setup.

Completed today:

1. Created / updated `data/obodesk_mvp_product_fact_verification_today.csv`.
2. Created `docs/OBODESK_PRODUCT_FACT_VERIFICATION_FIELD_GUIDE.md`.
3. Shopify Assistant completed read-only verification for 5 MVP product backend fields.
4. Codex wrote verified Shopify backend fields into the CSV working draft.
5. `Signature Monitor Riser` became sample row v0.1.
6. Confirmed live sellable size: `1000 × 260 × 122 mm`.
7. Confirmed live sellable color: `Walnut Brown`.
8. Removed health / medical risky claims such as neck protection and cervical relief.
9. Fixed CSV column misalignment using Python `csv` module.
10. Verified CSV structure: header = 41 columns, all 5 product rows = 41 columns.
11. No theme changes.
12. No Shopify changes.
13. No metafields created.
14. No Product Center import.
15. No Git commit.

Hui OS learnings:

1. AI Shopping readiness should be built on verified product facts, not AI-generated assumptions.
2. Shopify backend fields can be marked Verified when confirmed through Shopify Assistant read-only check.
3. Material, dimensions, load capacity, package contents, compatibility, and technical specs must come from supplier pages, 1688 links, supplier images, packaging, or physical product evidence.
4. Do not allow AI to invent product parameters.
5. Build one clean sample row first before scaling to all products.
6. For OboDesk, the correct workflow is: Shopify backend verification -> CSV working draft -> manual supplier fact verification -> risk wording cleanup -> Product Center / metafields only after facts are verified.
7. Core principle: verify first, structure second, automate third.

Next step:

- Continue manual supplier fact verification starting with `Premium Wool Felt Desk Mat`, using `Signature Monitor Riser` sample row v0.1 as the template.

## 2026-05-17 Hui OS v0.1 decision hypothesis loop

- Added `docs/decision_hypothesis_loop.md` as a Hui OS v0.1 method note.
- Recorded the method: `决策 -> 假设 -> 行动 -> 结果 -> 复盘 -> 认知修正`.
- Added the fixed `【决策假设闭环记录模板】`.
- Updated the working rule for long-feedback entrepreneurship tasks.
- No Hui OS module skeleton was changed.
- No Shopify theme files were changed.
- No product data was modified.
- No Shopify or Feishu API calls were made.

### Hui OS Note / 今日认知沉淀

Theme: 决策假设闭环记录法 / 与未来的自己对话.

Core learning:

1. 创业成长不是靠每天做很多事，而是靠持续校准自己的判断力。
2. 每一个重要决策都应该被记录成一个可验证的假设。
3. 记录的目的不是给别人看，也不是像大公司日报一样糊弄老板，而是写给未来的自己看。
4. 自己给自己写日报和复盘，本质上是自己是自己的老板，要对今天是否有收获负责。
5. 未来某一天回看今天的判断，可以检查当时的认知漏洞，从而获得真正的进步。
6. 这套方法特别适合 OboDesk、Product Center、Shopify 独立站、TikTok 内容、选品、品牌定位、自动化系统建设等长期反馈型任务。
7. Hui OS 不应该只记录今天做了什么，还要记录为什么这样做、期待什么变化、未来如何验证。

### Hui OS Working Rule

以后凡是涉及重要创业决策、产品决策、品牌决策、选品决策、网站结构调整、Product Center 字段设计、自动化系统建设、TikTok 内容方向测试，都不要只记录做了什么，还要记录：

1. 为什么做。
2. 期待什么变化。
3. 未来何时验证。
4. 用什么指标验证。
5. 复盘时认知是否需要修正。

Next step:

- 每天遇到重要决策时，使用 `docs/decision_hypothesis_loop.md` 中的 `【决策假设闭环记录模板】` 记录一条可回看的决策假设。

## 2026-05-17 AI Shopping Readiness v0.1 MVP5 supplier evidence closeout

- Completed supplier evidence supplementation for all 5 MVP Product Fact Verification v0.1 rows:
  - `Signature Monitor Riser`
  - `Premium Felt Desk Mat`
  - `RGB Monitor Light Bar`
  - `8-in-1 USB-C Hub`
  - `RGB Podcast Dynamic Microphone`
- Reviewed and accepted `data/obodesk_mvp_product_fact_verification_today.csv` as the current local Product Fact Verification working draft.
- Generated and reviewed `docs/OBODESK_MVP5_SAFE_PDP_DRAFT_V0.1.md` as the first English safe PDP copy draft for the 5 MVP products.
- Confirmed CSV structure:
  - 41 columns.
  - 5 product rows.
  - Each product row has 41 columns.
  - All 5 products keep `Need_Manual_Check = Yes`.
  - Most product rows now use `Partially Verified / Supplier Evidence Added`.
  - `Confidence_Level = Medium` for supplier-evidence rows.
- No Shopify theme files were changed.
- No Shopify backend data was written.
- No Shopify metafields were created.
- No Product Center formal table was modified.
- No Git commit was made.

### Product Fact Verification principles confirmed today

1. Product facts must be evidence-driven; do not fill parameters from common sense.
2. Shopify backend field `Verified` does not mean supplier facts are verified.
3. PDP copy should first be drafted as a safe local draft, not published directly.
4. High-risk claims must be explicitly listed under `Claims to Avoid`.
5. Product Center and Shopify metafields should wait until the PDP draft has passed manual review.

### Key risk boundaries

1. `Premium Felt Desk Mat`: do not use `Wool Felt`, `natural wool`, wool percentage, waterproof, stain-resistant, or heat-resistant claims.
2. `RGB Monitor Light Bar`: do not use eye-care, anti-blue-light, flicker-free, no glare, protect eyesight, or reduce eye strain claims.
3. `8-in-1 USB-C Hub`: do not use HDMI, 4K, 100W PD, fast charging, laptop charging, or universal compatibility claims.
4. `RGB Podcast Dynamic Microphone`: do not use studio-grade, noise cancellation, zero latency, universal compatibility, or simultaneous USB/XLR output claims.
5. `Signature Monitor Riser`: do not use neck protection, cervical relief, medical, health, or ergonomic treatment claims.

Next step:

- Manually review `docs/OBODESK_MVP5_SAFE_PDP_DRAFT_V0.1.md`.
- Pay special attention to whether `8-in-1 USB-C Hub` should move `15W-100W` from Technical Details into Evidence Gaps / Notes.
- After manual review, decide whether to generate a Product Center field sync draft.
- Do not create Shopify metafields yet.
- Do not write Shopify PDP content yet.

## 2026-05-19 Product Center sync review draft v0.1

- Completed manual review correction for `docs/OBODESK_MVP5_SAFE_PDP_DRAFT_V0.1.md`.
  - Moved the `8-in-1 USB-C Hub` `15W-100W` supplier-material range out of positive `Technical Details`.
  - Kept the `15W-100W` note only in `Evidence Gaps / Notes` to prevent misuse as a `100W PD` claim.
- Generated and reviewed `docs/OBODESK_MVP5_PRODUCT_CENTER_SYNC_DRAFT_V0.1.md`.
- Generated and corrected `data/obodesk_mvp5_product_center_sync_review_draft.csv`.
- Current review CSV status:
  - 34 columns.
  - 5 product rows.
  - `Ready_To_Import = No` for all rows.
  - `Product_Center_Write_Status = Review Draft Only` for all rows.
  - Can be used as Product Center pre-import manual review CSV v0.1.
- Fixed the key field-classification issue in `RGB Podcast Dynamic Microphone`:
  - Removed `Do not claim universal compatibility or compatibility with all devices.` from the `Compatibility` field.
  - Kept that risk warning in `Risk_Flag`, `Notes`, and `Claims_To_Avoid`.
  - `Compatibility` now contains only supplier-confirmed compatibility facts.
- No Shopify theme files were changed.
- No Shopify backend data was written.
- No Shopify metafields were created.
- No Feishu Product Center formal table was modified.
- No Feishu CLI write command was used.
- No Git commit was made.

### Product Center sync principles confirmed today

1. Product Center sync drafts must separate safe facts from risk-control notes.
2. `Technical_Specs` must not contain supplier ranges that can be misread as confirmed claims.
3. `Claims_To_Avoid`, `Risk_Flag`, `Evidence_Gaps`, and `Notes` are review-control fields, not positive PDP facts.
4. `Ready_To_Import` should remain `No` until human review decides field-level readiness.
5. Product Center formal sync and Shopify metafields should wait until the review CSV passes manual review.

Next step:

- Manually review `data/obodesk_mvp5_product_center_sync_review_draft.csv`.
- Decide which fields can enter a Feishu Product Center draft import version.
- Do not write the formal Product Center table yet.
- Do not create Shopify metafields yet.

## 2026-05-20 — OboDesk 证据化 MVP 工作底盘建立与目录治理

### 今日目标

- 将《创始人行动手册》的 AI-Native Startup 方法论接入 OboDesk 项目。
- 统一主工作目录。
- 建立证据化 MVP 阶段的上层方法论、文档索引和数据边界。
- 防止后续 Codex / Agent 误把草稿、CSV、AI 输出当成正式业务事实。

### 今日完成

- 将《创始人手册中文版.pdf》提取为：
  - `docs/reference/FOUNDERS_PLAYBOOK_CN_EXTRACT.md`
- 生成并小修：
  - `docs/OBODESK_AI_NATIVE_STARTUP_METHOD.md`
- 明确当前 OboDesk 阶段为：
  - 证据化 MVP 阶段，而不是发布阶段或规模化阶段。
- 统一后续主工作目录为：
  - `D:\My-AiOS\10_Workspace\WORK\shopify-projects\obodesk-shopify`
- 新增并小修 4 个证据化 MVP 配套文档：
  - `docs/OBODESK_PROBLEM_EVIDENCE_MAP.md`
  - `docs/OBODESK_MVP_SCOPE.md`
  - `docs/OBODESK_AGENTIC_WORKFLOW_DESIGN.md`
  - `docs/OBODESK_ADVERSARIAL_REVIEW_LOG.md`
- 完成只读目录盘点。
- 完成 workspace structure audit，并生成保存：
  - `docs/OBODESK_WORKSPACE_STRUCTURE_AUDIT_2026-05-20.md`
- 完成 `git status --short` 分组诊断。
- 新增：
  - `docs/INDEX.md`
- 新增：
  - `data/README.md`

### 今日关键判断

- OboDesk 当前已经具备 Shopify 独立站、Product Center、商品事实核验、Codex 工作流和文档底座。
- 但仍缺少足够真实市场证据，包括用户问题证据、内容转化证据、加购 / 购买证据、客服反馈、复购 / 推荐信号。
- 当前阶段重点不是继续扩大系统，而是补齐真实市场证据。
- 不应把页面完成度、Product Center 草稿、AI PDP 草稿、CSV review draft 或自动化能力误判为 PMF。
- 任何 Product Center 写入、Shopify 发布、CSV 导入、metafields 同步，都必须人工审阅。

### 已建立的事实源优先级

`Shopify commerce facts > supplier/physical evidence > Product Center reviewed records > local review drafts > AI draft content`

### 当前重要边界

- `data/obodesk_mvp_product_fact_verification_today.csv` 是 manual verification only。
- `data/obodesk_mvp5_product_center_sync_review_draft.csv` 是 review draft only，`Ready_To_Import = No`。
- `data/obodesk_mvp_product_fact_checklist.csv` 是历史 checklist。
- `data/obodesk_ai_pdp_p0_template.csv` 是 AI PDP P0 draft。
- 以上 CSV 均不得直接导入 Product Center、同步 Shopify metafields 或作为正式 PDP 文案来源。
- 当前确认 `.codex-lark-read-json/` 属于工具缓存，不进入 Git。
- 当前确认 `data/obodesk_mvp_product_fact_checklist.csv` 只是 CSV 引号格式变化，不进入今天提交。

### 明天建议继续

- 基于 `docs/OBODESK_PROBLEM_EVIDENCE_MAP.md`，围绕 5 个 MVP 产品和 3 个核心场景制定第一轮真实市场证据收集计划。
- 5 个 MVP 产品：
  - Signature Monitor Riser
  - Premium Wool Felt Desk Mat
  - RGB Monitor Light Bar
  - 8-in-1 USB-C Hub
  - RGB Podcast Dynamic Microphone
- 3 个核心场景：
  - AI / 远程办公桌面
  - 视频会议 / 内容创作桌面
  - 桌面收纳与设备集成
- 下一步先做只读计划，不要改 Shopify，不要导入 Product Center，不要启动复杂自动化。

### 今日收尾状态

- 今日仅新增 / 更新 Markdown 文档。
- 未修改代码。
- 未修改 Shopify theme。
- 未修改 Product Center 数据。
- 未修改 CSV 内容。
- 未运行 Shopify / 飞书写入操作。
- 当前确认没有 Shopify theme 代码变更。
- 当前确认没有写入飞书。
- 当前确认没有导入 Product Center。
- 主项目已具备证据化 MVP 工作底盘，可以进入真实市场证据收集阶段。

### 最终收尾状态

- 已完成三个 commit：
  - `fd70dbd document evidence-based mvp operating context`
  - `93f51db add product fact review data boundaries`
  - `fade99d chore: ignore local lark cache files`
- 当前 `git status --short` 无输出，工作区干净。
- 今日未修改 Shopify theme。
- 今日未写入飞书。
- 今日未导入 Product Center。
- 今日任务收尾完成。

## 2026-05-31 Desk Mat safe wording and Shopify update prep

- Confirmed current work priority remains evidence-based MVP and product fact safety, not additional automation.
- Reviewed live Desk Mat URL behavior:
  - `/products/obodesk-premium-wool-felt-desk-mat` returns 200.
  - `/products/obodesk-premium-felt-desk-mat` returns 404 before Shopify Admin handle change.
- Corrected the local homepage Featured Essentials Desk Mat card:
  - `Essential Wool Desk Mat` -> `Essential Desk Mat`.
  - Copy changed to safer wording.
  - Link kept on the currently valid old handle to avoid publishing a 404.
- Updated the local fact verification worksheet for Desk Mat with stricter safe wording and claim boundaries.
- Added `docs/OBODESK_DESK_MAT_SAFE_SHOPIFY_UPDATE_2026-05-31.md` as the human Shopify Admin update packet for title, PDP copy, SEO, and future handle/redirect decision notes.
- Added the new update packet to `docs/INDEX.md`.
- Ran `shopify.cmd theme check`; result: 45 files inspected, no offenses found.
- Attempted to open Shopify Admin product editing through Chrome, but the session reached Shopify Accounts login/selection flow and was not stable for automated editing.
- Local safe wording preparation is complete in the CSV, documentation, and homepage card copy.
- Shopify Admin has not been manually saved with this Desk Mat update.
- Later browser review reached the Shopify product page, but the operation was stopped before save; Codex did not click Save and did not write any Shopify Admin fields.
- No Shopify Admin product data was changed by Codex.
- No Shopify metafields were created.
- No Product Center data was imported or written.

Next step:

- In Shopify Admin, manually update only the Desk Mat title, PDP description, SEO title, and SEO description using `docs/OBODESK_DESK_MAT_SAFE_SHOPIFY_UPDATE_2026-05-31.md`.
- Keep the current live handle `obodesk-premium-wool-felt-desk-mat` for this round. Handle and redirect decisions remain a separate future task.

## 2026-06-03 — Live Theme Emergency Recovery Completed

### Incident Summary

Original target:
Only hide Kits from the top navigation.

Actual mistake:
The following 3 Section files were synchronized to the Live Theme:

- `sections/header.liquid`
- `sections/featured-products.liquid`
- `sections/footer.liquid`

Key risks:

- The local theme directory and the real online Live Theme structure were not fully aligned.
- `featured-products.liquid` and `footer.liquid` contained accumulated local changes from earlier work.
- Shopify CLI previously warned:
  `It doesn't seem like you're running this command in a theme directory.`
- Live Theme synchronization continued after the warning appeared.
- No unpublished preview theme was created before publish.
- No remote Live Theme backup was duplicated before publish.
- The operation did not follow the rule of uploading only one file at a time with immediate manual QA after each upload.

### Impact

The online homepage changed beyond the intended scope.

Later review found that the Live Theme code editor was missing:

- `sections/header.liquid`
- `sections/featured-products.liquid`
- `sections/footer.liquid`

At the same time, `templates/index.json` still referenced `featured-products`.

### Recovery Process

1. Paused all write operations.
2. Read-only verified the correct store:
   `obo-5.myshopify.com`
3. Read-only verified the original Live Theme:
   `OboDesk V1 Local Build`
   Theme ID: `153947996300`
4. Created the isolated recovery directory:
   `rollback-backups/recovery-preview-662f7f6`
5. Pulled the current online theme.
6. Restored the 3 missing Section files from Git commit `662f7f6`.
7. Ran `theme check`:
   `45 files inspected with no offenses found.`
8. Uploaded the unpublished recovery preview theme:
   `OboDesk Recovery Preview 662f7f6`
   Theme ID: `155001913484`
9. User manually approved the preview.
10. Duplicated the incorrect Live Theme before publishing recovery:
    `OboDesk backup before recovery publish`
    Theme ID: `155002241164`
    Status: `unpublished`
11. Published the recovery theme:
    `OboDesk Recovery Preview 662f7f6`
    Theme ID: `155001913484`
    Status: `live`
12. User manually opened `https://obodesk.com` and confirmed the homepage was restored.

### Recovery Boundary

This round did not:

- Run a new `theme push` against the Live Theme.
- Modify formal theme files.
- Modify Shopify Pages.
- Modify products.
- Modify inventory.
- Modify product publication status.
- Modify Handles.
- Create Redirects.
- Modify Feishu.
- Create a new Git commit.
- Push to GitHub.

### Root Cause

The root cause was not a single code defect. It was a release process without enough production safety guardrails:

1. Multiple files were synchronized to the Live Theme at once.
2. Differences between the local theme and online theme were not audited.
3. The CLI warning did not trigger a stop.
4. No remote backup was created.
5. No unpublished preview was created.
6. No single-file release with step-by-step manual QA was used.
7. No complete deployment log was kept.

### Follow-Up Constraints

- Pause theme batch synchronization.
- Before the Live Theme and local theme differences are audited, batch `theme push` is forbidden.
- Modify only one theme file at a time.
- Upload only one theme file at a time.
- Perform immediate manual QA after every upload.
- Stop immediately when any CLI warning appears.
- Duplicate the Live Theme before every publish.
- Upload an unpublished preview theme before every publish.
- After every publish, record Store, Theme ID, files, commands, and QA result.

## 2026-06-03 — Live Theme Difference Audit Completed

- Completed the read-only difference audit between the current Live Theme and local formal theme directory.
- Current Live Theme:
  - `OboDesk Recovery Preview 662f7f6`
  - Theme ID: `155001913484`
  - Status: `live`
- Audit directory:
  - `rollback-backups/live-theme-audit-155001913484`
- Online file count: 52.
- Local formal theme file count: 62.
- Matching file count: 44.
- Difference file count: 19.
- Batch `theme push` remains frozen.
- Only `sections/header.liquid` may enter the next single-file unpublished preview release process.
- `sections/featured-products.liquid` and `sections/footer.liquid` already match the Live Theme and should not be synced again for this incident.
- No online write operation was executed.
- No local formal theme file was modified.

## 2026-06-13 - Build to Validation status checkpoint

User-reported completion:

1. Theme state confirmation.
2. Cold Visitor Test.
3. Cart / Checkout validation.
4. Monitor Riser fact audit.
5. Evidence Log V1.
6. Validation Content V1.

Local artifacts created during this checkpoint:

- `docs/OBODESK_MONITOR_RISER_FACT_CHECK_2026-06-13.md`
- `docs/OBODESK_MARKET_EVIDENCE_LOG_V1.md`
- `docs/OBODESK_MONITOR_RISER_VALIDATION_CONTENT_V1.md`
- `OBODESK_MONITOR_RISER_DAY1_CLAIM_REVIEW_DRAFT.md`
- `data/obodesk_monitor_riser_14day_validation_log_draft.csv`
- `docs/OBODESK_MONITOR_RISER_14DAY_VALIDATION_PLAN_DRAFT.md`
- `docs/OBODESK_SHOPIFY_COLD_VISITOR_MANUAL_TEST_CHECKLIST_DRAFT.md`

Current project stage:

- Build -> Validation.

Boundary:

- No Shopify theme publish was performed.
- No Shopify product data was modified.
- No Shopify metafields were created.
- No Product Center import or formal write was performed.
- No automation was enabled.
- Validation files are local manual evidence and content draft materials only.

Next best step:

- Run the first manual validation cycle for `Signature Monitor Riser`, record real evidence in `docs/OBODESK_MARKET_EVIDENCE_LOG_V1.md` or `data/obodesk_monitor_riser_14day_validation_log_draft.csv`, and avoid new build work unless a P0 storefront blocker is confirmed.

## 2026-06-14 - Validation operating index update

- OboDesk has moved from Build to Validation.
- Current operating focus: `Signature Monitor Riser 14-Day Validation`.
- Daily priorities:
  - Record real market evidence.
  - Check PDP / Add to cart / Checkout / PayPal path health when needed.
  - Record TikTok content feedback, comments, DMs, add-to-cart, checkout, and orders.
  - Avoid unrelated build work.
- This round only reorganized the documentation index and daily workflow note.
- No Shopify Admin operation was performed.
- No theme file was modified.
- No theme publish was performed.
- No file was moved.
- No Git commit was made.
