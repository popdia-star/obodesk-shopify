# OboDesk Shopify Theme 日常工作流

## 项目名称

OboDesk Shopify Theme

## 当前 live theme 状态

当前主题处于 V1 搭建后的检查和小范围优化阶段。首页、Collection 页面、Product 页面、Cart 页面已经完成基础版本，Header 导航已回退为 5 个 collection 导航。

首页和购物车中的 All Products 链接已完成修复，并已提交、推送到 live theme。正式站 `obodesk.com` 已验证生效。

正式站产品 `Test Desk Product` 已验证可以进入 checkout，Checkout 页面显示商品 `$1.00`，PayPal 支付入口正常显示。Product → Cart/Add → Checkout 主链路基本跑通。

## 已完成事项

- 首页 V1
- Collection 页面 V1
- Product 页面 V1
- Cart 页面 V1
- Header 导航已回退为 5 个 collection 导航
- 首页和购物车 All Products 链接修复
  - Hero Explore essentials 改为 Desk Setup collection
  - Featured Essentials 卡片链接改为 Desk Setup / Lighting collection
  - Footer CTA Explore all essentials 改为 Desk Setup collection
  - Empty cart Explore essentials 改为 Desk Setup collection
  - 修改已提交并推送到 live theme
  - 正式站 `obodesk.com` 验证已生效
- 购买闭环验证
  - 正式站产品 `Test Desk Product` 可以进入 checkout
  - Checkout 页面显示商品 `$1.00`
  - PayPal 支付入口正常显示
  - Product → Cart/Add → Checkout 主链路基本跑通

## 当前待办事项

- 运行 theme check
- 本地预览检查首页 / collection / product / cart
- 根据检查结果再做小范围修复
- Product 页面后续优化 available / Sold out / disabled 状态显示
- 后续再排查是否存在偶发 POST 422 /cart/add
- 当前不建议立刻修改 `product.liquid`，避免影响已跑通的购买链路

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
