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
