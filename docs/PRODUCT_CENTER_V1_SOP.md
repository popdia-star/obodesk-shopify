# Product Center v1.0 SOP

更新日期：2026-05-07

## 一、当前阶段状态

- Product Center v1.0 已建立。
- Products_SPU 当前 7 行。
- SKU_Variants 当前 13 行。
- Product_Images 当前 7 行。
- MVP5 Baseline 已导入。
- CoreBatch2 Lighting 已合并。
- 正式表在飞书显示正常。

## 二、当前系统定位

- Shopify 是真实销售数据源，负责承载线上商品、价格、库存、上架状态、变体 ID、产品 URL 和主图等销售事实。
- 飞书是标准化产品资产中枢，负责承载 SPU/SKU 规范、运营分组、内容状态、审核状态、SEO/内容/视频规划字段和后续任务协同。
- Codex 负责本地清洗、校验、合并文件，输出可人工检查和导入飞书的 CSV/XLSX/报告。
- 人工负责最终检查 Excel/CSV、确认字段逻辑、导入飞书临时表，并在校验通过后合并正式表。
- 当前阶段暂不使用飞书 API 自动写入正式表。

## 三、日常上新流程

1. 1688 选品。
2. 店小秘采集并推送 Shopify。
3. Shopify 后台整理为 Draft / Active。
4. Shopify 导出最新产品数据。
5. Codex 生成 Product Center 导入文件。
6. Codex 输出校验报告。
7. 人工检查 Excel / CSV。
8. 导入飞书临时表。
9. 校验通过后合并正式表。
10. 更新 Import_Log。

## 四、字段主从关系

### Shopify 为准字段

- Shopify_Product_ID
- Shopify_Variant_ID
- Shopify_Handle
- Shopify_Product_URL
- Shopify_Title
- Shopify_Vendor
- Shopify_Product_Type
- Shopify_Real_SKU
- Shopify_Price
- Shopify_Compare_At_Price
- Shopify_Inventory_Qty
- Shopify_Requires_Shipping
- Shopify_Available_For_Sale
- Online_Store_Published
- Main_Image_URL

### 飞书为准字段

- SPU_ID
- SKU_ID
- Product_Line
- Run_Scope
- Product_Status
- Product_Type
- Variant_SKU
- Review_Status
- Notes
- SEO / content / video planning fields

## 五、Import_Log 表设计

建议字段：

- Import_ID
- Import_Date
- Batch_Name
- Source
- Products_Count
- Variants_Count
- Images_Count
- Input_File
- Output_File
- Import_Status
- Checked_By
- Check_Result
- Notes

历史记录建议：

| Import_ID | Import_Date | Batch_Name | Source | Products_Count | Variants_Count | Images_Count | Import_Status | Check_Result | Notes |
| --- | --- | --- | --- | ---: | ---: | ---: | --- | --- | --- |
| IMP-20260507-MVP5 | 2026-05-07 | MVP5 Baseline | Shopify export + Codex local clean | 5 | 7 | 5 | Imported | PASS | Live Core MVP baseline products imported into Product Center v1.0. |
| IMP-20260507-BATCH2-LIGHTING | 2026-05-07 | CoreBatch2 Lighting | Shopify assistant export + Codex local merge | 2 | 6 | 2 | Merged | PASS | Lighting batch merged into formal v1.0 table; Shopify_Real_SKU Chinese suffix preserved for later SKU standardization. |

## 六、QA 视图建议

### Products_SPU 视图

- Live Core MVP
- Core Candidate
- Needs Shopify Fix
- Missing Shopify ID
- Missing Image
- Needs SEO

### SKU_Variants 视图

- All Active Variants
- Missing Variant ID
- Missing Inventory
- Missing Price
- Chinese Shopify SKU
- Empty Shopify Real SKU
- Duplicate SKU Check

### Product_Images 视图

- Main Images
- Missing Alt Text
- Pending Alt Review
- Missing Image URL

## 七、下一阶段路线

### 阶段 1：手工 Shopify 导出 + Codex 清洗

继续使用 Shopify 导出或 Shopify 助理整理出的最新商品数据，由 Codex 在本地生成导入文件、校验报告和合并文件。人工检查后导入飞书。

### 阶段 2：Codex 固化为本地脚本

将当前 MVP5、CoreBatch2、合并校验流程沉淀为可复用本地脚本，固定输入目录、输出目录、字段校验、重复校验和报告格式，减少每批处理的人为差异。

### 阶段 3：n8n 读取 Shopify API 写入飞书临时表

在字段规则稳定后，由 n8n 读取 Shopify API，把最新商品、变体、价格、库存、图片等事实字段写入飞书临时表。正式表仍保留人工确认或半自动合并机制。

### 阶段 4：Agent 根据飞书 Product Center 自动生成 SEO / 内容 / 视频 / 修复任务

基于飞书 Product Center 的标准化数据，让 Agent 自动识别缺口并生成 SEO、商品文案、图片 Alt、视频脚本、产品修复任务和运营优先级建议。
