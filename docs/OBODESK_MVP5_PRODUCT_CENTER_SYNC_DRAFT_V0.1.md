# OboDesk MVP5 Product Center Sync Draft v0.1

Updated: 2026-05-19

Sources:
- `data/obodesk_mvp_product_fact_verification_today.csv`
- `docs/OBODESK_MVP5_SAFE_PDP_DRAFT_V0.1.md`

Boundary:
- Draft for manual review only.
- Not imported into Feishu Product Center.
- Not written to Shopify.
- Not used to create Shopify metafields.
- Missing Evidence fields are marked `Need Review` or `Do Not Sync`.
- High-risk claims are listed under `Do Not Sync Claims`.

## 1. Signature Monitor Riser

### 一、Product Identity

- Product_Title current value: Signature Monitor Riser
- Recommended_Safe_Title: Signature Monitor Riser
- Product_Handle: `signature-monitor-riser-live`
- Shopify_Product_ID: `9195405803660`
- SKU / Variant_Name / Variant_ID: `OBODESK-RISER-SIG` / `Default Title` / `47999451725964`
- Rename recommended: No
- Rename reason: Current title does not contain unsupported material, health, medical, or technical claims.

### 二、Safe Product Facts

- Material: Need Manual Review.
- Dimensions: 1000 x 260 x 122 mm.
- Color_Options: Walnut Brown.
- Package_Includes: Need Manual Review.
- Compatibility: Compatible with desktop monitor and laptop desk setups where size and load fit; exact load capacity and fit require confirmation.
- Key_Features: Raises a monitor above the desk surface; frees desk surface space; creates under-riser keyboard or small item storage; supports organized desktop setup.
- Technical_Specs: Non-electronic monitor riser; physical specs require supplier confirmation.

### 三、Product Center 建议字段映射

| Product Center 字段名建议 | 来源字段 | 建议写入内容 | 写入状态 | 原因 |
| --- | --- | --- | --- | --- |
| product_title | Product_Title / Safe PDP draft | Signature Monitor Riser | Ready | Title is safe and already used in Shopify. |
| product_handle | Product_Handle | signature-monitor-riser-live | Ready | Shopify verified field. |
| shopify_product_id | Shopify_Product_ID | 9195405803660 | Ready | Shopify verified field. |
| variant_sku | SKU | OBODESK-RISER-SIG | Ready | Shopify verified field. |
| variant_name | Variant_Name | Default Title | Need Review | Consider explicit size/color variant naming before sync. |
| variant_id | Variant_ID | 47999451725964 | Ready | Shopify verified field. |
| safe_title | Safe PDP draft | Signature Monitor Riser | Ready | No rename required. |
| material | Material | Need Manual Review | Do Not Sync | Exact material evidence is missing. |
| dimensions | Dimensions | 1000 x 260 x 122 mm | Ready | Supplier-backed live sellable size. |
| color_options | Color_Options | Walnut Brown | Ready | Supplier-backed live sellable color. |
| package_includes | Package_Includes | Requires confirmation | Do Not Sync | Package contents are missing. |
| compatibility | Compatibility | Desktop monitor and laptop desk setups where size and load fit | Need Review | Load capacity and fit still require confirmation. |
| key_features | Key_Features / Safe PDP draft | Raises monitor; frees desk surface space; creates under-riser storage | Need Review | Avoid ergonomic/health wording. |
| technical_specs | Technical_Specs | Non-electronic riser; physical specs require confirmation | Need Review | Material and load capacity missing. |
| claims_to_avoid | Risky_Claims_To_Avoid | Medical/health/ergonomic claims; neck protection; cervical relief; universal monitor compatibility; exact load capacity before confirmed | Ready | Risk boundaries are explicit. |
| evidence_gaps | Missing_Fields | Load capacity; material; package contents; source screenshot archive | Ready | Must remain visible before downstream sync. |

### 四、Do Not Sync Claims

- neck protection
- cervical relief
- medical benefit
- ergonomic health benefit
- health benefit
- universal monitor compatibility
- exact load capacity before confirmed

### 五、Evidence Gaps

- Load capacity.
- Exact material evidence.
- Package contents evidence.
- Source screenshot archive.
- Shopify variant naming decision.

### 六、Sync Decision

Ready for Product Center draft review.

Reason: Core size and color are verified, but material, load capacity, and package contents must remain `Need Review` / `Do Not Sync`.

## 2. Premium Felt Desk Mat

### 一、Product Identity

- Product_Title current value: Premium Wool Felt Desk Mat
- Recommended_Safe_Title: Premium Felt Desk Mat
- Product_Handle: `obodesk-premium-wool-felt-desk-mat`
- Shopify_Product_ID: `9063444873356`
- SKU / Variant_Name / Variant_ID: `FELT-MAT-M-GRY; FELT-MAT-L-GRY; FELT-MAT-XL-GRY` / `Medium (80cmx40cm); Large (90cmx45cm); Extra Large (100cmx50cm)` / `46880944783500; 46880944816268; 46880944849036`
- Rename recommended: Yes
- Rename reason: Current Shopify title contains unsupported wool claim. Supplier evidence confirms felt / felt-style material, not wool content, natural wool, or wool percentage.

### 二、Safe Product Facts

- Material: Felt surface with dotted anti-slip backing.
- Dimensions: Medium 80 x 40 cm; Large 90 x 45 cm; Extra Large 100 x 50 cm.
- Color_Options: Dark Gray only for current Shopify listing.
- Package_Includes: Desk mat only; no additional accessories confirmed.
- Compatibility: Suitable for desks, writing tables, dining tables, computer workstations, and keyboard/mouse desk setups.
- Key_Features: Dark gray felt / felt-style surface; dotted anti-slip backing; 3 mm thickness; three current Shopify size options.
- Technical_Specs: Thickness 3 mm; sizes 80 x 40 cm, 90 x 45 cm, 100 x 50 cm; dark gray; dotted anti-slip backing.

### 三、Product Center 建议字段映射

| Product Center 字段名建议 | 来源字段 | 建议写入内容 | 写入状态 | 原因 |
| --- | --- | --- | --- | --- |
| product_title_current | Product_Title | Premium Wool Felt Desk Mat | Need Review | Existing Shopify title contains unsupported wool claim. |
| safe_title | Safe PDP draft / Risk_Flag | Premium Felt Desk Mat | Ready | Safer title avoids unsupported wool claim. |
| product_handle | Product_Handle | obodesk-premium-wool-felt-desk-mat | Ready | Shopify verified field. |
| shopify_product_id | Shopify_Product_ID | 9063444873356 | Ready | Shopify verified field. |
| variant_sku | SKU | FELT-MAT-M-GRY; FELT-MAT-L-GRY; FELT-MAT-XL-GRY | Ready | Shopify verified field. |
| variant_name | Variant_Name | Medium 80x40 cm; Large 90x45 cm; Extra Large 100x50 cm | Ready | Matches current Shopify size options. |
| variant_id | Variant_ID | 46880944783500; 46880944816268; 46880944849036 | Ready | Shopify verified field. |
| material | Material | Felt surface with dotted anti-slip backing | Ready | Supplier evidence supports felt and dotted backing. |
| dimensions | Dimensions | 80 x 40 cm; 90 x 45 cm; 100 x 50 cm | Ready | Supplier-confirmed current listing sizes. |
| thickness | Technical_Specs | 3 mm | Ready | Supplier-confirmed current listing thickness. |
| color_options | Color_Options | Dark Gray only for current listing | Ready | Supplier-confirmed current listing color. |
| package_includes | Package_Includes | Desk mat only; no additional accessories confirmed | Need Review | Package method is not fully confirmed. |
| compatibility | Compatibility | Desks, writing tables, dining tables, computer workstations, keyboard/mouse desk setups | Ready | Safe non-health usage scope. |
| key_features | Key_Features | Dark gray felt-style surface; dotted anti-slip backing; 3 mm thickness; three size options | Ready | All are supplier-supported facts. |
| wool_content | Missing_Fields | Missing Evidence | Do Not Sync | Wool percentage/natural wool evidence missing. |
| waterproof_status | Missing_Fields | Missing Evidence | Do Not Sync | Waterproof/water-resistant evidence missing. |
| cleaning_guidance | Missing_Fields | Missing Evidence | Do Not Sync | Cleaning guidance not confirmed. |
| claims_to_avoid | Risky_Claims_To_Avoid | wool felt; natural wool; 100% wool; wool percentage; waterproof; water-resistant; stain-resistant; heat-resistant; anti-fatigue; ergonomic benefit; health benefit | Ready | Must be visible to prevent unsafe copy. |
| evidence_gaps | Missing_Fields | Wool percentage; natural wool evidence; waterproof/water-resistant/stain/heat evidence; cleaning guidance; full packaging method | Ready | Needed for future verification. |

### 四、Do Not Sync Claims

- wool felt
- natural wool
- 100% wool
- wool percentage
- waterproof
- water-resistant
- stain-resistant
- heat-resistant
- anti-fatigue
- ergonomic benefit
- health benefit

### 五、Evidence Gaps

- Wool percentage.
- Natural wool evidence.
- Waterproof or water-resistant evidence.
- Stain-resistant evidence.
- Heat-resistant evidence.
- Cleaning guidance.
- Full packaging method evidence.

### 六、Sync Decision

Ready for Product Center draft review.

Reason: The current safe facts are usable if the Product Center title uses `Premium Felt Desk Mat` and unsupported wool/waterproof/health claims are not synced.

## 3. RGB Monitor Light Bar

### 一、Product Identity

- Product_Title current value: RGB Monitor Light Bar
- Recommended_Safe_Title: RGB Monitor Light Bar
- Product_Handle: `rgb-monitor-light-bar`
- Shopify_Product_ID: `9246445863052`
- SKU / Variant_Name / Variant_ID: `811623636370_51CM/自动光感/RGB多模式/全光谱/Ra97/无线遥控; 811623636370_41CM/Ra80` / `51CM/RGB Multi-Mode/Ra97/Wireless; 41CM/Ra80` / `48484507582604; 48484520591500`
- Rename recommended: No
- Rename reason: Title is category/feature based and does not contain eye-care, medical, or universal-fit claims.

### 二、Safe Product Facts

- Material: Variant-specific. P3E uses metal body according to supplier attributes. P3 PRO MAX is shown as aluminum alloy + ABS / acrylic in supplier materials.
- Dimensions: P3E 41 cm. P3 PRO MAX 51 cm; supplier parameter image shows light body diameter 20 x 510 mm.
- Color_Options: Need Manual Review.
- Package_Includes: P3E includes light bar, mounting bracket/clamp, USB power cable, and user manual; remote and battery not included. P3 PRO MAX includes light bar, mounting bracket/clamp, wireless remote, one remote battery, USB power cable, and user manual.
- Compatibility: Compatible with flat monitors, curved monitors, and narrow-bezel monitors. Exact monitor thickness range requires confirmation.
- Key_Features: P3E 41 cm, Ra >= 80, 5W, body touch controls, three color temperature modes. P3 PRO MAX 51 cm, Ra >= 97, 9W, 2.4G wireless remote, RGB rear ambient lighting, automatic light sensing, three color temperature modes.
- Technical_Specs: See variant-specific power, Ra, length, controls, RGB, USB powered, and color temperature notes. P3 PRO MAX middle color temperature has a 3800K vs 4000K conflict.

### 三、Product Center 建议字段映射

| Product Center 字段名建议 | 来源字段 | 建议写入内容 | 写入状态 | 原因 |
| --- | --- | --- | --- | --- |
| product_title | Product_Title | RGB Monitor Light Bar | Ready | Safe title. |
| safe_title | Safe PDP draft | RGB Monitor Light Bar | Ready | No rename required. |
| product_handle | Product_Handle | rgb-monitor-light-bar | Ready | Shopify verified field. |
| shopify_product_id | Shopify_Product_ID | 9246445863052 | Ready | Shopify verified field. |
| variant_sku | SKU | Existing two SKU values | Need Review | SKU contains Chinese characters; channel sync risk. |
| variant_mapping | Variant_Name / Notes | 41CM/Ra80 = P3E; 51CM/RGB/Ra97/Wireless = P3 PRO MAX | Ready | Supplier-confirmed mapping. |
| variant_id | Variant_ID | 48484507582604; 48484520591500 | Ready | Shopify verified field. |
| material | Material | P3E metal body; P3 PRO MAX aluminum alloy + ABS / acrylic | Ready | Supplier-supported variant-specific facts. |
| dimensions | Dimensions | P3E 41 cm; P3 PRO MAX 51 cm; light body diameter 20 x 510 mm | Ready | Supplier parameter evidence. |
| color_options | Color_Options | Need Manual Review | Do Not Sync | Not confirmed. |
| package_includes | Package_Includes | Variant-specific package contents | Ready | Supplier-confirmed package contents. |
| compatibility | Compatibility | Flat monitors, curved monitors, narrow-bezel monitors | Need Review | Exact monitor thickness range missing; no universal fit claim. |
| key_features | Key_Features | Variant-specific controls, Ra values, power, RGB rear ambient lighting, automatic sensing | Ready | Supplier-supported, with risky claims excluded. |
| technical_specs | Technical_Specs | P3E: 41 cm, 5W, Ra >= 80, 3100K/4200K/6400K. P3 PRO MAX: 51 cm, 9W, Ra >= 97, USB powered, 2.4G remote, RGB rear lighting | Need Review | P3 PRO MAX middle color temperature conflict remains. |
| certification_notes | Notes / Missing_Fields | CE/FCC evidence stronger; RoHS P3 PRO MAX model match requires confirmation | Need Review | Certification model matching incomplete. |
| claims_to_avoid | Risky_Claims_To_Avoid | eye-care; anti-blue-light; flicker-free; protect eyesight; universal fit; health/medical claims | Ready | Required risk boundary. |
| evidence_gaps | Missing_Fields | Thickness range; color temperature conflict; RoHS match; eye-care support; brightness; cable length; cleaning; warranty | Ready | Must remain visible. |

### 四、Do Not Sync Claims

- eye-care
- anti-blue-light
- blue-light exemption
- flicker-free
- no glare
- protect eyesight
- reduce eye strain
- health benefit
- medical or ergonomic benefit
- universal monitor fit
- fits all monitors
- color accuracy claims
- unconfirmed brightness claims
- waterproof
- heat-resistant

### 五、Evidence Gaps

- Exact compatible monitor thickness range.
- Final confirmation of P3 PRO MAX middle color temperature: 3800K vs 4000K.
- Final RoHS model match for P3 PRO MAX.
- Independent support for eye-care / blue-light / flicker-free claims.
- Brightness data.
- Cable length.
- Cleaning guidance.
- Warranty / after-sales information.

### 六、Sync Decision

Ready for Product Center draft review.

Reason: Core model mapping, package contents, and main specs are supplier-supported. Some technical and certification fields must remain `Need Review`.

## 4. 8-in-1 USB-C Hub

### 一、Product Identity

- Product_Title current value: 8-in-1 USB-C Hub
- Recommended_Safe_Title: 8-in-1 Dual-Connector USB Hub
- Product_Handle: `obodesk-8-in-1-usb-c-hub`
- Shopify_Product_ID: `8323641376908`
- SKU / Variant_Name / Variant_ID: `69593581` / `Default Title` / `44804263837836`
- Rename recommended: Recommended for clarity
- Rename reason: Current supplier-confirmed variant is a dual-connector no-HDMI spec. Safer title avoids implying HDMI, 4K, or 100W PD.

### 二、Safe Product Facts

- Material: ABS and aluminum alloy housing.
- Dimensions: Product size 14.5 x 2.8 x 1 cm; integrated cable length 13.5 cm.
- Color_Options: Need Manual Review.
- Package_Includes: Paper box packaging; includes 1 USB hub unit. No additional accessories confirmed.
- Compatibility: Supports common USB peripherals such as keyboard, mouse, USB drive, external storage, card reader, printer, cooling fan, drawing tablet, and game controller. Device and system compatibility may vary.
- Key_Features: 8-in-1 dual-connector USB hub with USB-A and USB-C host connectors; USB 3.0; three USB 2.0 ports; SD; TF/microSD; 3.5 mm audio; USB-C; PD charging support.
- Technical_Specs: USB 3.0 up to 5 Gbps; USB 2.0 up to 480 Mbps; product weight 49 g; package weight 57 g; PD charging support confirmed, maximum wattage not confirmed.

### 三、Product Center 建议字段映射

| Product Center 字段名建议 | 来源字段 | 建议写入内容 | 写入状态 | 原因 |
| --- | --- | --- | --- | --- |
| product_title_current | Product_Title | 8-in-1 USB-C Hub | Need Review | Safe but less specific than current dual-connector spec. |
| safe_title | Safe PDP draft | 8-in-1 Dual-Connector USB Hub | Ready | Clarifies current variant and avoids HDMI/4K implication. |
| product_handle | Product_Handle | obodesk-8-in-1-usb-c-hub | Ready | Shopify verified field. |
| shopify_product_id | Shopify_Product_ID | 8323641376908 | Ready | Shopify verified field. |
| variant_sku | SKU | 69593581 | Need Review | Confirm SKU source. |
| variant_name | Variant_Name | Default Title | Need Review | Current Product Center may need explicit variant spec. |
| variant_id | Variant_ID | 44804263837836 | Ready | Shopify verified field. |
| material | Material | ABS and aluminum alloy housing | Ready | Supplier-confirmed. |
| dimensions | Dimensions | 14.5 x 2.8 x 1 cm; cable length 13.5 cm | Ready | Supplier-confirmed. |
| color_options | Color_Options | Need Manual Review | Do Not Sync | Not confirmed. |
| port_list | Key_Features / Notes | USB 3.0; 3 x USB 2.0; SD; TF/microSD; 3.5 mm audio; USB-C; USB-A and USB-C host connectors | Ready | Supplier-confirmed current variant. |
| package_includes | Package_Includes | Paper box packaging; 1 USB hub unit; no additional accessories confirmed | Ready | Supplier-confirmed. |
| compatibility | Compatibility | Common USB peripherals; device/system compatibility may vary | Need Review | OS/device compatibility details missing. |
| technical_specs | Technical_Specs / Safe PDP draft | USB 3.0 up to 5 Gbps; USB 2.0 up to 480 Mbps; PD support, max wattage requires confirmation; weight data | Need Review | Transfer speed supported; PD max wattage and USB-C details missing. |
| pd_power_range_note | Safe PDP Evidence Gaps | Supplier materials mention 3A-4A and 15W-100W, but max PD wattage is not confirmed for this exact variant | Need Review | Do not write as positive Product Center tech spec. |
| hdmi_fields | Risky_Claims_To_Avoid | Do not sync HDMI / 4K HDMI | Do Not Sync | Current confirmed variant has no HDMI claim. |
| claims_to_avoid | Risky_Claims_To_Avoid | HDMI; 4K; 100W PD; fast charging; laptop charging; universal compatibility; guaranteed speed; advanced heat dissipation | Ready | Required risk boundary. |
| evidence_gaps | Missing_Fields | Max PD wattage; USB-C function; OS compatibility; plug-and-play; certification match; warranty | Ready | Must remain visible. |

### 四、Do Not Sync Claims

- HDMI output
- 4K HDMI
- 100W PD charging unless confirmed for this exact variant
- fast charging
- laptop charging
- universal compatibility
- works with all devices
- guaranteed transfer speed
- overheating prevention
- advanced heat dissipation
- professional-grade performance

### 五、Evidence Gaps

- Maximum PD wattage for this exact 8-in-1 dual-connector variant.
- Supplier materials mention a 3A-4A current range and 15W-100W power range, but the maximum PD charging wattage for this exact 8-in-1 dual-connector variant is not confirmed. Do not claim 100W PD charging unless supplier confirmation is obtained.
- Exact USB-C port function details.
- Compatible operating systems.
- Plug-and-play support.
- Certification model match.
- Warranty / after-sales information.

### 六、Sync Decision

Ready for Product Center draft review.

Reason: Core current-variant facts are usable, but PD wattage, USB-C function, OS compatibility, plug-and-play, and certification fields must remain `Need Review`.

## 5. RGB Podcast Dynamic Microphone

### 一、Product Identity

- Product_Title current value: RGB Podcast Dynamic Microphone
- Recommended_Safe_Title: NV7 RGB Dynamic Microphone
- Product_Handle: `obodesk-usb-streaming-pc-microphone`
- Shopify_Product_ID: `8323639869580`
- SKU / Variant_Name / Variant_ID: `58034253` / `ME4` / `44804257906828`
- Rename recommended: Recommended for model clarity
- Rename reason: Supplier confirms current listing is NV7 regular black version. Safe title uses confirmed model and avoids studio/broadcast claims.

### 二、Safe Product Facts

- Material: Missing Evidence. Exact housing material requires supplier confirmation.
- Dimensions: Product dimensions 222 x 83 x 88 mm. Current listing is regular black version. Regular package size 31 x 13 x 10 cm, 952 g. Do not use arm-stand package dimensions.
- Color_Options: Current listing black regular version. Supplier also lists white and arm-stand versions, but they are not part of current listing.
- Package_Includes: Microphone, user manual and retail box, 3/8 inch to 5/8 inch adapter nut, USB-C to USB-A data cable, USB-A to USB-C adapter.
- Compatibility: Supplier confirms plug-and-play driver-free setup and compatibility with Windows, macOS, iOS, Android, PS5, and PS4. Do not claim universal compatibility.
- Key_Features: NV7 dynamic microphone; cardioid pickup pattern; RGB lighting; mute button; GAIN knob; MONITOR knob; USB/USB-C/XLR used separately; 3.5 mm headphone monitoring jack; real-time monitoring; 270 degree rotating mounting arm; 3/8 inch to 5/8 inch mount compatibility.
- Technical_Specs: Model NV7; dynamic; cardioid; 5V; 5W; no built-in battery; USB/USB-C/XLR used separately; frequency response, sensitivity, sample rate/bit depth, impedance, SPL, cable length, and housing material remain unverified.

### 三、Product Center 建议字段映射

| Product Center 字段名建议 | 来源字段 | 建议写入内容 | 写入状态 | 原因 |
| --- | --- | --- | --- | --- |
| product_title_current | Product_Title | RGB Podcast Dynamic Microphone | Need Review | Safe enough, but model-specific title is clearer. |
| safe_title | Safe PDP draft | NV7 RGB Dynamic Microphone | Ready | Supplier-confirmed model, avoids risky claims. |
| product_handle | Product_Handle | obodesk-usb-streaming-pc-microphone | Ready | Shopify verified field. |
| shopify_product_id | Shopify_Product_ID | 8323639869580 | Ready | Shopify verified field. |
| variant_sku | SKU | 58034253 | Ready | Shopify verified field. |
| variant_name | Variant_Name | ME4 | Need Review | Shopify variant does not match supplier model naming. |
| variant_id | Variant_ID | 44804257906828 | Ready | Shopify verified field. |
| model | Technical_Specs / Notes | NV7 | Ready | Supplier-confirmed. |
| color_options | Color_Options | Current listing black regular version | Ready | Supplier-confirmed current listing. |
| material | Material | Missing Evidence | Do Not Sync | Housing material missing. |
| dimensions | Dimensions | Product 222 x 83 x 88 mm; regular package 31 x 13 x 10 cm, 952 g | Ready | Supplier-confirmed for regular listing. |
| package_includes | Package_Includes | Microphone; manual/box; 3/8 to 5/8 adapter nut; USB-C to USB-A cable; USB-A to USB-C adapter | Ready | Supplier-confirmed. |
| compatibility | Compatibility | Windows, macOS, iOS, Android, PS5, PS4; plug-and-play driver-free supplier-confirmed | Ready | Supplier-confirmed, with no universal compatibility claim. |
| connection_types | Technical_Specs | USB, USB-C, XLR used separately | Ready | Supplier-confirmed; simultaneous output excluded. |
| monitoring | Technical_Specs | 3.5 mm headphone monitoring jack; real-time monitoring | Ready | Supplier-confirmed; zero-latency not claimed. |
| audio_specs | Missing_Fields | Frequency response, sensitivity, sample rate/bit depth, impedance, SPL missing | Do Not Sync | Missing technical evidence. |
| certifications | Notes | Supplier confirms CE / FCC / RoHS coverage for NV7 | Need Review | Safe as supplier-confirmed note; avoid legal/platform compliance guarantees. |
| claims_to_avoid | Risky_Claims_To_Avoid | studio-grade; broadcast-quality; lossless audio; noise cancellation; zero latency; universal compatibility; simultaneous USB/XLR output | Ready | Required risk boundary. |
| evidence_gaps | Missing_Fields | Housing material; audio specs; cable length; warranty | Ready | Must remain visible. |

### 四、Do Not Sync Claims

- studio-grade
- professional broadcast quality
- broadcast-quality
- lossless audio
- noise cancellation
- noise reduction
- zero latency monitoring
- low latency
- universal compatibility
- compatible with all devices
- USB and XLR simultaneous output
- works with all phones
- works with all computers
- professional recording quality
- high fidelity audio

### 五、Evidence Gaps

- Exact housing material.
- Frequency response.
- Sensitivity.
- Sample rate / bit depth.
- Impedance.
- Maximum SPL.
- Cable length.
- Warranty / after-sales information.

### 六、Sync Decision

Ready for Product Center draft review.

Reason: Current listing model, configuration, package contents, compatibility, and core controls are supplier-confirmed. Missing audio specs and material must remain `Do Not Sync` or `Need Review`.

## Cross-Product Sync Summary

### Ready Fields

- Shopify identity fields: Product handle, Shopify Product ID, SKU, Variant ID.
- Safe title recommendations.
- Supplier-confirmed dimensions for current listing scopes.
- Supplier-confirmed color/configuration where available.
- Package contents for Premium Felt Desk Mat, RGB Monitor Light Bar, 8-in-1 USB-C Hub, and RGB Podcast Dynamic Microphone.
- Risk boundaries / Claims to Avoid for all 5 products.

### Need Review Fields

- Signature Monitor Riser: material, load capacity, package contents, variant naming.
- Premium Felt Desk Mat: full packaging method, cleaning guidance, any wool/waterproof/stain/heat claims.
- RGB Monitor Light Bar: color options, monitor thickness range, P3 PRO MAX middle color temperature, RoHS P3 PRO MAX match, brightness, cable length.
- 8-in-1 USB-C Hub: PD max wattage, USB-C port function, OS compatibility, plug-and-play support, certification match.
- RGB Podcast Dynamic Microphone: Shopify variant naming vs NV7, housing material, audio specs, cable length, warranty.

### Do Not Sync Fields

- Missing Evidence fields.
- High-risk marketing or compliance claims.
- Any unsupported health, medical, ergonomic, waterproof, eye-care, charging wattage, HDMI/4K, audio quality, or universal compatibility claims.
