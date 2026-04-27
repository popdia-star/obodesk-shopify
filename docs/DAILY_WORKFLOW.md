# OboDesk Shopify Theme 日常工作流

## 项目名称

OboDesk Shopify Theme

## 当前 live theme 状态

当前主题处于 V1 搭建后的检查阶段。首页、Collection 页面、Product 页面、Cart 页面已经完成基础版本，Header 导航已回退为 5 个 collection 导航。

## 已完成事项

- 首页 V1
- Collection 页面 V1
- Product 页面 V1
- Cart 页面 V1
- Header 导航已回退为 5 个 collection 导航

## 当前待办事项

- 运行 theme check
- 本地预览检查首页 / collection / product / cart
- 修复首页和购物车中仍跳向 all_products 的入口
- 根据检查结果再做小范围修复

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
