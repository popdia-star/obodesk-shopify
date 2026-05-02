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
