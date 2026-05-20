# OboDesk Product Fact Verification Field Guide

Updated: 2026-05-14

This guide explains the bilingual columns planned for `data/obodesk_mvp_product_fact_verification_today.csv`. The CSV is for manual product fact verification only. It must not be imported into Product Center, synced to Shopify metafields, or used for storefront display until product facts are checked and approved.

## Field Guide

| Field | Meaning and Filling Rule |
| --- | --- |
| Product_Handle / 商品Handle | Shopify product handle. Confirm from Shopify Admin product URL. Do not guess or clean handles without a redirect plan. |
| Product_Title / 商品标题 | Product title. Confirm from Shopify Admin first, then compare with Product Center naming. |
| SKU / SKU | Variant SKU. Confirm from Shopify Admin variant data or product export. Do not invent SKU values. |
| Variant_Name / 变体名称 | Variant option name, such as size or color. Confirm from Shopify Admin. |
| Product_Type / 商品类型 | Product category/type. Can be drafted from current content, but final value should be checked against Shopify Admin and product positioning. |
| Vendor / 品牌/供应商 | Shopify vendor or supplier/brand name. Confirm from Shopify Admin or supplier sheet. |
| Shopify_Product_URL / Shopify商品链接 | Full Shopify product URL. Confirm from Shopify Admin or live storefront. |
| Is_Live_Core_MVP / 是否Live Core MVP | Whether this product belongs to the 5-product Live Core MVP set. Confirm from project records and Shopify Admin. |
| Online_Store_Status / 在线商店状态 | Online Store publication status. Confirm from Shopify Admin. |
| Material / 材质 | Product material. Confirm from 1688 source product, supplier sheet, product images, packaging, or physical sample. Do not let AI guess material. |
| Dimensions / 尺寸 | Product dimensions. Confirm from 1688 source product, supplier sheet, packaging, or physical measurement. Do not estimate from images. |
| Color_Options / 颜色选项 | Available product colors. Confirm from Shopify variants, product images, supplier sheet, or physical sample. |
| Compatibility / 兼容性 | Compatible devices, monitor sizes, ports, or use conditions. Confirm from supplier documentation or physical testing. Do not claim universal compatibility. |
| Package_Includes / 包装清单 | Items included in the package. Confirm from supplier sheet, packaging information, product images, or physical sample. |
| Key_Features / 核心卖点 | Verified product features suitable for PDP. Must be backed by source evidence before storefront use. |
| Target_User / 目标用户 | Intended user groups. Can come from AI draft, but should be reviewed manually for accuracy and audience fit. |
| Use_Scenario / 使用场景 | Practical use scenarios. Can come from AI draft, but should be reviewed against real product capability. |
| Technical_Specs / 技术参数 | Technical specs such as ports, wattage, frequency response, lighting modes, or load capacity. Must come from supplier documentation, Shopify product facts, packaging, or testing. AI must not guess these values. |
| Risky_Claims_To_Avoid / 需避免的风险表述 | Claims that should not be used unless verified, such as medical, health, waterproof, eye-care, studio-grade, broadcast-quality, exact wattage, speed, or universal compatibility claims. |
| Evidence_Source / 证据来源 | Source used for verification, such as Shopify Admin, 1688 source product, supplier sheet, physical sample, product images, or packaging information. |
| Confidence_Level / 可信度 | Suggested values: `Low`, `Medium`, `High`. Keep `Low` until facts are verified from reliable sources. |
| Need_Manual_Check / 是否需要人工核验 | Use `Yes` until the row has been manually checked and approved. |
| Missing_Fields / 缺失字段 | Fields that are not yet available and must be filled before Product Center import or metafield planning. |
| Unclear_Fields / 不确定字段 | Fields that have draft assumptions or ambiguous information and need confirmation. |
| Verification_Status / 核验状态 | Suggested values: `Pending`, `In Review`, `Verified`, `Needs Fix`, `Do Not Use`. Default is `Pending`. |
| Notes / 备注 | Operational notes, blockers, or cautions for the product record. |

## Source Rules

- Confirm from Shopify Admin: `Product_Handle`, `Product_Title`, `SKU`, `Variant_Name`, `Vendor`, `Shopify_Product_URL`, `Is_Live_Core_MVP`, `Online_Store_Status`, and Shopify-side product type.
- Confirm from 1688 / supplier sheet / product images / packaging / physical sample: `Material`, `Dimensions`, `Color_Options`, `Compatibility`, `Package_Includes`, `Key_Features`, and `Technical_Specs`.
- AI may draft audience and scenario fields, but humans must review `Target_User`, `Use_Scenario`, `Key_Features`, and all risk-sensitive wording.
- AI must not guess material, dimensions, wattage, transfer speed, display output, load capacity, polar pattern, frequency response, waterproof status, heat resistance, medical benefits, eye-care benefits, or universal compatibility.

## Current Workflow Boundary

- Do not modify the Shopify theme.
- Do not modify `product.liquid`.
- Do not create Shopify metafields.
- Do not import this CSV into Product Center.
- Do not use this CSV for frontend PDP display.
- Use this file only as a manual fact verification worksheet.
