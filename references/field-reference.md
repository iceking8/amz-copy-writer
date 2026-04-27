# Amazon CLR 报告字段参考

> 来源：Category Listing Report (CLR) + 库存文件模板（Inventory File Template）

---

## 📊 标准 CLR 报告字段映射

> 从 Seller Central → Reports → Category Listing Reports 下载

### 核心字段（所有类目通用）

| 字段名 | Local Label | 必填 | 说明 |
|--------|-------------|------|------|
| `::listing_status` | Status | ✅ | Active/Inactive |
| `::title` | Title | ✅ | 产品标题（只读） |
| `contribution_sku#1.value` | SKU | ✅ | 卖家 SKU |
| `product_type#1.value` | Product Type | ✅ | 产品类型（DRESS/SHIRT 等） |
| `::record_action` | Listing Action | ⚪ | Create/Replace/Delete |
| `parentage_level[marketplace_id=ATVPDKIKX0DER]#1.value` | Parentage Level | ⚠️ | Parent/Child |
| `child_parent_sku_relationship[marketplace_id=ATVPDKIKX0DER]#1.parent_sku` | Parent SKU | ⚠️ | 子 SKU 关联的父 SKU |
| `variation_theme#1.name` | Variation Theme Name | ⚠️ | 变体主题（如 Size/Color） |

### 产品标识（Product Identity）

| 字段名 | Local Label | 必填 | 说明 |
|--------|-------------|------|------|
| `item_name[marketplace_id=ATVPDKIKX0DER][language_tag=en_US]#1.value` | Item Name | ✅ | 产品标题 |
| `brand[marketplace_id=ATVPDKIKX0DER][language_tag=en_US]#1.value` | Brand Name | ✅ | 品牌名称 |
| `amzn1.volt.ca.product_id_type` | Product Id Type | ✅ | UPC/EAN/ASIN |
| `amzn1.volt.ca.product_id_value` | Product Id | ✅ | 产品 ID 值 |
| `item_type_keyword[marketplace_id=ATVPDKIKX0DER]#1.value` | Item Type Keyword | ✅ | 商品类型关键词 |
| `model_number[marketplace_id=ATVPDKIKX0DER]#1.value` | Model Number | ⚠️ | 型号 |
| `model_name[marketplace_id=ATVPDKIKX0DER][language_tag=en_US]#1.value` | Model Name | ⚠️ | 型号名称 |

### 内容字段（Content）

| 字段名 | Local Label | 必填 | 说明 |
|--------|-------------|------|------|
| `product_description[marketplace_id=ATVPDKIKX0DER][language_tag=en_US]#1.value` | Product Description | ✅ | 产品描述 |
| `bullet_point[...][language_tag=en_US]#1.value` | Bullet Point 1 | ✅ | 五点描述 1 |
| `bullet_point[...][language_tag=en_US]#2.value` | Bullet Point 2 | ✅ | 五点描述 2 |
| `bullet_point[...][language_tag=en_US]#3.value` | Bullet Point 3 | ✅ | 五点描述 3 |
| `bullet_point[...][language_tag=en_US]#4.value` | Bullet Point 4 | ✅ | 五点描述 4 |
| `bullet_point[...][language_tag=en_US]#5.value` | Bullet Point 5 | ✅ | 五点描述 5 |
| `generic_keyword[marketplace_id=ATVPDKIKX0DER][language_tag=en_US]#1.value` | Generic Keywords | ⚪ | 搜索关键词 |

### 图片字段（Images）

| 字段名 | Local Label | 说明 |
|--------|-------------|------|
| `main_product_image_locator[marketplace_id=ATVPDKIKX0DER]#1.media_location` | 主图 URL | 主产品图 |
| `other_product_image_locator_1[...]#1.media_location` | 附图 1 | 其他产品图 |
| `other_product_image_locator_2[...]#1.media_location` | 附图 2 | 其他产品图 |
| `other_product_image_locator_3-8[...]` | 附图 3-8 | 最多 8 张 |
| `swatch_product_image_locator[...]#1.media_location` | 色块图 | 变体专用 |

### 价格字段（Offer）

| 字段名 | Local Label | 说明 |
|--------|-------------|------|
| `list_price[marketplace_id=ATVPDKIKX0DER]#1.value` | List Price | 标准价格 |
| `purchasable_offer[...][audience=ALL]#1.our_price#1...` | Our Price | 售价 |
| `purchasable_offer[...][audience=B2B]#1.our_price#1...` | B2B Price | B2B 价格 |

### 颜色/尺码字段

| 字段名 | Local Label | 说明 |
|--------|-------------|------|
| `color[marketplace_id=ATVPDKIKX0DER][language_tag=en_US]#1.value` | Color | 颜色名称 |
| `color[...][language_tag=en_US]#1.standardized_values#1` | Standardized Color | 标准化颜色 |
| `apparel_size[marketplace_id=ATVPDKIKX0DER]#1.size_system` | Size System | 尺码系统（US/EU/UK） |
| `apparel_size[...]#1.size_class` | Size Class | 尺码类型 |
| `apparel_size[...]#1.size` | Size | 尺码值 |
| `apparel_size[...]#1.size_to` | Size To | 尺码范围 |
| `apparel_size[...]#1.body_type` | Body Type | 体型（Regular/Petite/Plus） |
| `apparel_size[...]#1.height_type` | Height Type | 身高类型（Regular/Petite/Tall） |

### 材质字段

| 字段名 | Local Label | 说明 |
|--------|-------------|------|
| `material[marketplace_id=ATVPDKIKX0DER][language_tag=en_US]#1.value` | Material 1 | 材质 1 |
| `material[...][language_tag=en_US]#2.value` | Material 2 | 材质 2 |
| `material[...][language_tag=en_US]#3.value` | Material 3 | 材质 3 |
| `fabric_type[marketplace_id=ATVPDKIKX0DER][language_tag=en_US]#1.value` | Fabric Type | 面料类型 |

### 合规字段（Compliance）

| 字段名 | Local Label | 必填 | 说明 |
|--------|-------------|------|------|
| `country_of_origin[marketplace_id=ATVPDKIKX0DER]#1.value` | Country of Origin | ✅ | 原产国 |
| `supplier_declared_dg_hz_regulation[...]#1.value` | Dangerous Goods Regulations | ✅ | 危险品法规 |
| `fabric_type[marketplace_id=ATVPDKIKX0DER][language_tag=en_US]#1.value` | Fabric Type | ✅ | 面料类型（服装类必填） |

---

## 📋 必填字段清单（CLR 报告）

### 所有类目通用必填字段

| Local Label | 字段类型 | 说明 |
|-------------|----------|------|
| Status | 枚举 | Active/Inactive |
| Title | 文本 | 产品标题 |
| SKU | 文本 | 卖家 SKU |
| Product Type | 枚举 | 产品类型 |
| Item Name | 文本 | 产品标题 |
| Brand Name | 文本 | 品牌名称 |
| Product Id Type | 枚举 | UPC/EAN/ASIN |
| Item Type Keyword | 文本 | 商品类型关键词 |
| Product Description | 文本 | 产品描述 |
| Bullet Point | 文本 | 五点描述 |
| Fabric Type | 文本 | 面料类型（服装类） |
| Country of Origin | 枚举 | 原产国 |
| Dangerous Goods Regulations | 枚举 | 危险品法规 |

### 条件必填字段（变体产品）

| Local Label | 条件 | 说明 |
|-------------|------|------|
| Parentage Level | 变体系列 | Parent 或 Child |
| Parent SKU | Child SKU 必填 | 关联的父 SKU |
| Variation Theme Name | 变体系列 | 如 Size/Color |
| Product Id | 新建产品 | UPC/EAN/JAN |

---

## 🗂️ 字段分组统计

| 分组 | 字段数量 | 说明 |
|------|----------|------|
| Product Details | 103 | 产品详情属性 |
| Safety & Compliance | 84 | 安全合规属性 |
| Offer | 23 | 报价属性 |
| Offer (US) | 23 | 美国市场报价 |
| Product Identity | 22 | 产品标识 |
| Shipping | 16 | 物流属性 |
| Images | 10 | 图片属性 |
| Listing Identity | 3 | Listing 标识 |
| Variations | 3 | 变体属性 |
| Reference Group | 2 | 参考属性 |

---

# 库存文件模板字段参考（旧格式）

> 来源：DRESS 类目库存文件模板（Inventory File Template）

## 字段分类

### 📌 必填字段 (Required)

这些字段必须填写，否则无法创建 listing。

| 字段名 | 中文说明 | 字段类型 |
|--------|----------|----------|
| `feed_product_type` | 产品类型 | 枚举 |
| `item_sku` | 卖家 SKU | 文本 |
| `brand_name` | 品牌名称 | 文本 |
| `item_name` | 产品标题 | 文本（≤200字符） |
| `external_product_id` | 产品 ID（UPC/EAN/JAN 等） | 文本 |
| `external_product_id_type` | 产品 ID 类型 | 枚举（EAN/UPC/JAN） |
| `item_type` | 商品类型关键词 | 枚举（来自 BTG） |
| `standard_price` | 标准价格 | 数字 |
| `main_image_url` | 主图片 URL | URL |

---

### 🔖 基础信息 (Basic)

| 字段名 | 中文说明 | 必填 | 备注 |
|--------|----------|------|------|
| `feed_product_type` | 产品类型 | ✅ | 如 `shoes`, `shirt`, `dress` |
| `item_sku` | 卖家 SKU | ✅ | 唯一标识符 |
| `brand_name` | 品牌名称 | ✅ | 需符合 Amazon 品牌政策 |
| `item_name` | 产品标题 | ✅ | ≤200字符，不含特殊符号 |
| `manufacturer` | 制造商 | ⚪ | 默认等于品牌名 |
| `external_product_id` | 产品 ID | ✅ | UPC/EAN/JAN |
| `external_product_id_type` | ID 类型 | ✅ | EAN/UPC/JAN |
| `item_type` | 商品类型关键词 | ✅ | 来自 Browse Tree Guide |
| `part_number` | 制造商零件号 | ⚪ | MPN |
| `model_name` | 型号名称 | ⚪ | |
| `model_year` | 型号年份 | ⚪ | |
| `catalog_number` | 目录编号 | ⚪ | |
| `product_description` | 产品描述 | ⚪ | 详细描述文字 |

---

### 🔍 发现/搜索优化 (Discovery)

用于提升搜索可见性和转化率。

| 字段名 | 中文说明 | 必填 | 备注 |
|--------|----------|------|------|
| `bullet_point1` - `bullet_point5` | 五点描述 | ⚠️ | 强烈建议填写，RUFUS 评分关键 |
| `generic_keywords` | 搜索词 | ⚪ | 后台关键词 |
| `platinum_keywords1` - `platinum_keywords5` | 白金关键词 | ⚪ | 高级功能 |
| `target_audience_base1` - `target_audience_base3` | 目标受众 | ⚪ | |
| `target_audience_keywords1` - `target_audience_keywords5` | 受众关键词 | ⚪ | |
| `specific_uses_keywords1` - `specific_uses_keywords5` | 用途关键词 | ⚪ | |
| `thesaurus_attribute_keywords1` - `thesaurus_attribute_keywords5` | 属性关键词 | ⚪ | |
| `thesaurus_subject_keywords1` - `thesaurus_subject_keywords5` | 主题关键词 | ⚪ | |

---

### 🎨 产品丰富度 (Product Enrichment)

| 字段名 | 中文说明 | 必填 | 备注 |
|--------|----------|------|------|
| `color_name` | 颜色名称 | ⚠️ | 变体系列常用 |
| `color_map` | 颜色映射 | ⚪ | 标准化颜色值 |
| `size_name` | 尺码名称 | ⚠️ | 变体系列常用 |
| `size_map` | 尺码映射 | ⚪ | 标准化尺码值 |
| `material_type` | 材质类型 | ⚪ | |
| `outer_material_type1` - `outer_material_type5` | 外层材质 | ⚪ | |
| `fabric_type1` - `fabric_type5` | 面料类型 | ⚪ | |
| `inner_material_type` | 内层材质 | ⚪ | |
| `style_name` | 风格名称 | ⚪ | |
| `pattern_name` | 图案 | ⚪ | |
| `occasion` | 场合 | ⚪ | |
| `occasion_type1` - `occasion_type5` | 场合类型 | ⚪ | |
| `department_name` | 部门 | ⚠️ | 如 Women/Men/Unisex |
| `target_gender` | 目标性别 | ⚠️ | Male/Female/Unisex |
| `age_range_description` | 年龄范围 | ⚪ | 如 adult/teen/child |
| `care_instructions1` - `care_instructions4` | 洗护说明 | ⚪ | |

---

### 📐 尺寸与规格 (Dimensions)

| 字段名 | 中文说明 | 单位字段 |
|--------|----------|----------|
| `item_display_length` | 产品长度 | `item_display_length_unit_of_measure` |
| `item_display_width` | 产品宽度 | `item_display_width_unit_of_measure` |
| `item_display_height` | 产品高度 | `item_display_height_unit_of_measure` |
| `item_display_weight` | 产品重量 | `item_display_weight_unit_of_measure` |
| `item_display_diameter` | 产品直径 | `item_display_diameter_unit_of_measure` |
| `volume_capacity_name` | 容量 | `volume_capacity_name_unit_of_measure` |
| `liquid_volume` | 液体体积 | `liquid_volume_unit_of_measure` |

**服装特定尺寸：**
| 字段名 | 中文说明 |
|--------|----------|
| `chest_size` | 胸围 |
| `chest_size_unit_of_measure` | 胸围单位 |
| `cup_size` | 罩杯 |
| `neck_size` | 领围 |
| `sleeve_length` | 袖长 |
| `shirt_size` | 衬衫尺码 |
| `shirt_size_system` | 尺码系统（US/EU/UK 等） |
| `shirt_size_class` | 尺码类型（Alpha/Numeric） |

**鞋类特定尺寸：**
| 字段名 | 中文说明 |
|--------|----------|
| `footwear_size_system` | 鞋码系统 |
| `footwear_age_group` | 年龄组 |
| `footwear_size_class` | 尺码类型 |
| `footwear_width` | 鞋宽 |
| `footwear_size` | 鞋码 |
| `heel_height` | 鞋跟高度 |
| `shaft_height` | 靴筒高度 |
| `boot_opening_circumference` | 靴口周长 |

---

### 📦 物流与包装 (Fulfillment)

| 字段名 | 中文说明 | 备注 |
|--------|----------|------|
| `package_height` | 包装高度 | |
| `package_width` | 包装宽度 | |
| `package_length` | 包装长度 | |
| `package_weight` | 包装重量 | |
| `fulfillment_center_id` | FFC ID | FBA 专用 |
| `fulfillment_latency` | 处理时间 | 天数 |
| `merchant_shipping_group_name` | 运费模板 | |

---

### ⚖️ 合规与安全 (Compliance)

| 字段名 | 中文说明 | 备注 |
|--------|----------|------|
| `country_of_origin` | 原产国 | |
| `legal_disclaimer_description` | 法律免责声明 | |
| `safety_warning` | 安全警告 | |
| `cpsia_cautionary_statement1` - `cpsia_cautionary_statement4` | CPSIA 警告 | 儿童产品 |
| `california_proposition_65_compliance_type` | 加州 65 号提案合规 | |
| `california_proposition_65_chemical_names1` - `california_proposition_65_chemical_names5` | 涉及化学品名称 | |
| `required_product_compliance_certificate` | 产品合规证书 | |
| `safety_data_sheet_url` | SDS 安全数据表 URL | |

**电池相关：**
| 字段名 | 中文说明 |
|--------|----------|
| `are_batteries_included` | 是否含电池 |
| `batteries_required` | 是否需要电池 |
| `battery_type1` - `battery_type3` | 电池类型 |
| `number_of_batteries1` - `number_of_batteries3` | 电池数量 |
| `battery_cell_composition` | 电池成分 |
| `lithium_battery_energy_content` | 锂电池能量含量 |
| `lithium_battery_packaging` | 锂电池包装 |

---

### 💰 报价与价格 (Offer)

| 字段名 | 中文说明 | 必填 | 备注 |
|--------|----------|------|------|
| `standard_price` | 标准价格 | ✅ | |
| `currency` | 货币 | ✅ | USD/EUR 等 |
| `list_price` | 建议零售价 | ⚪ | MSRP |
| `sale_price` | 促销价 | ⚪ | |
| `sale_from_date` | 促销开始日期 | ⚪ | |
| `sale_end_date` | 促销结束日期 | ⚪ | |
| `map_price` | 最低广告价 | ⚪ | MAP |
| `quantity` | 库存数量 | ✅ | |
| `condition_type` | 商品状况 | ⚪ | New/Used 等 |
| `condition_note` | 状况说明 | ⚪ | |
| `max_order_quantity` | 最大订购量 | ⚪ | |
| `handling_time` | 处理时间 | ⚪ | 天数 |

---

### 🖼️ 图片 (Images)

| 字段名 | 中文说明 | 备注 |
|--------|----------|------|
| `main_image_url` | 主图片 URL | ✅ 必填，纯白背景 |
| `other_image_url1` - `other_image_url8` | 附加图片 URL | 最多 8 张 |
| `swatch_image_url` | 色块图片 | 变体专用 |
| `other_image_url` | 其他图片 | |

**图片标准：**
- 主图必须纯白背景（RGB 255,255,255）
- 产品必须占图片面积 85% 以上
- 不允许文字、logo、水印、插图
- 支持 JPEG、TIFF、GIF 格式

---

### 🔗 变体关系 (Variation)

| 字段名 | 中文说明 | 备注 |
|--------|----------|------|
| `parent_child` | 父子关系 | parent/child |
| `parent_sku` | 父 SKU | 子 SKU 填写 |
| `relationship_type` | 关系类型 | variation |
| `variation_theme` | 变体主题 | 如 SizeName-ColorName |

---

### 🔄 更新操作 (Update/Delete)

| 字段名 | 中文说明 | 值 |
|--------|----------|-----|
| `update_delete` | 更新/删除 | Update/Delete |

---

## 字段类型说明

| 类型 | 说明 |
|------|------|
| ✅ Required | 必填字段 |
| ⚠️ Strongly Recommended | 强烈建议填写 |
| ⚪ Optional | 选填字段 |

---

## 注意事项

1. **标题限制**：≤200 字符，不含 HTML、特殊字符（`*`, `/`, `?` 等）
2. **品牌政策**：品牌名需可验证，否则需申请豁免
3. **产品 ID**：需要有效的 UPC/EAN/JAN，无条码需申请豁免
4. **变体**：同一变体系列必须使用相同的 `variation_theme`
5. **图片**：主图必须纯白背景，产品占 85% 以上

---

## 相关资源

- [Browse Tree Guide (BTG)](https://sellercentral.amazon.com/gp/help/1641)
- [图片标准](https://sellercentral.amazon.com/gp/help/1881)
- [品牌名称政策](https://sellercentral.amazon.com/help/hub/reference/G2N3GKE5SGSHWYRZ)
