# Amazon COSMO 知识图谱系统

> 来源：COSMO: A Large-Scale E-commerce Common Sense Knowledge Generation and Serving System at Amazon (SIGMOD 2024)

## 概述

COSMO 是 Amazon 的大规模电商常识知识图谱系统，用于从用户行为中挖掘用户意图，支持搜索、推荐等下游应用。

---

## 核心概念

### 用户行为类型

| 行为类型 | 定义 | 示例 |
|----------|------|------|
| **search-buy** | 用户搜索关键词后购买商品 | 搜索 "winter coat" → 购买 "Long Sleeve Puffer Coat" |
| **co-buy** | 用户同时购买的商品对 | 相机包 + 屏幕保护玻璃 |

### 常识知识三元组

```
(behavior, relation, tail)
```

**示例：**
- (购买相机包+屏幕保护玻璃, capableOf, 提供相机保护)
- (孕妇鞋, require, 防滑)

---

## 15 种电商常识关系

| 关系类型 | 尾实体类型 | 示例 |
|----------|-----------|------|
| `used_for_func` | 功能/用途 | dry face |
| `used_for_eve` | 事件/活动 | walk the dog |
| `used_for_aud` | 目标受众 | daycare worker |
| `capable_of` | 功能/用途 | hold snacks |
| `used_to` | 功能/用途 | build a fence |
| `used_as` | 概念/产品类型 | smart watch |
| `is_a` | 概念/产品类型 | normal suit |
| `used_on` | 时间/季节/事件 | late winter |
| `used_in_loc` | 地点/场所 | bedroom |
| `used_in_body` | 身体部位 | sensitive skin |
| `used_with` | 互补产品 | surface cover |
| `used_by` | 目标受众 | cat owner |
| `xIntersted_in` | 兴趣 | herbal medicine |
| `xIs_a` | 目标受众 | pregnant women |
| `xWant` | 活动 | play tennis |

---

## 知识质量评估

### 双指标评估体系

| 指标 | 定义 | 说明 |
|------|------|------|
| **Plausibility** | 合理性 | 知识是否符合常识逻辑 |
| **Typicality** | 典型性 | 知识是否能代表典型购物行为 |

### 质量评估五问法

为了降低标注者的认知负担，将评估分解为五个问题：

1. **完整性**：解释是否为完整句子？
2. **相关性**：解释是否相关？
3. **信息量**：解释是否有信息量？
4. **合理性**：解释是否合理？(Plausibility)
5. **典型性**：解释是否典型？(Typicality)

### 典型 vs 非典型示例

| 产品 | 非典型解释（差） | 典型解释（好） |
|------|-----------------|----------------|
| Apple Watch | "因为它是一种手表" | "因为它是智能手表，可以追踪健康数据" |
| 共同购买 | "因为顾客喜欢它们" | "因为它们可以一起提供保护功能" |

---

## 对 Listing 优化的启示

### 1. Bullet Point 写作原则

根据 COSMO 的发现，高质量的 bullet point 应该：

**✅ 好的做法：**
- 描述**具体功能和使用场景**（used_for_func, used_for_eve）
- 明确**目标受众**（used_for_aud, used_by）
- 突出**典型用途**而非泛泛而谈

**❌ 避免：**
- 泛泛的描述（"因为顾客喜欢它"）
- 循环定义（"Apple Watch 是一种手表"）
- 无信息量的废话

### 2. 搜索语义差距

COSMO 发现用户搜索词与产品描述之间存在**语义差距**：

```
用户搜索: "winter coat"
产品标题: "Long Sleeve Puffer Coat"
差距: 用户需求 vs 产品描述
```

**优化建议：**
- 标题和描述中包含**用户搜索意图相关的关键词**
- 使用用户语言而非专业术语
- 覆盖**常见使用场景和目的**

### 3. 目标受众识别

COSMO 的关系类型中有多个与受众相关：
- `used_for_aud` - 功能针对的受众
- `used_by` - 使用者
- `xIs_a` - 受众身份

**优化建议：**
- 在 bullet point 中明确指出目标受众
- 使用受众熟悉的语言和场景描述

---

## 统计数据

| 指标 | 数值 |
|------|------|
| 覆盖类目 | 18 个主要类目 |
| 知识节点 | 6.3M |
| 知识边 | 29M |
| 关系类型 | 15 种 |
| 标注指令 | 30k |

---

## 18 个覆盖类目

1. Clothing, Shoes & Jewelry
2. Sports & Outdoors
3. Home & Kitchen
4. Patio, Lawn & Garden
5. Tools & Home Improvement
6. Musical Instruments
7. Industrial & Scientific
8. Automotive
9. Electronics
10. Baby Products
11. Arts, Crafts & Sewing
12. Health & Household
13. Toys & Games
14. Video Games
15. Grocery & Gourmet Food
16. Office Products
17. Pet Supplies
18. Others

---

## 下游应用

COSMO 已部署于以下 Amazon 搜索应用：

1. **搜索相关性**：判断搜索词与产品的相关性
2. **会话推荐**：基于用户行为的推荐
3. **搜索导航**：引导用户找到想要的产品

---

## 对 CLR 审查的启发

### 检查项补充

基于 COSMO 的发现，可以在 CLR 审查中增加：

| 检查项 | 说明 |
|--------|------|
| Bullet 典型性 | Bullet 是否描述了典型用途，而非泛泛而谈 |
| 目标受众覆盖 | 是否明确指出目标受众 |
| 使用场景覆盖 | 是否覆盖常见使用场景 |
| 语义差距 | 标题/描述是否包含用户搜索意图相关词 |

### RUFUS 评分关联

COSMO 的发现支持 RUFUS 评分框架：

- **Bullet 1 (Hero Benefit)** → `capable_of`, `used_for_func`
- **Bullet 2 (Target Audience)** → `used_for_aud`, `used_by`, `xIs_a`
- **Bullet 3 (Differentiation)** → 典型性 vs 竞品

---

## Answer-to-Product Matching 流程

从买家查询到产品推荐的完整流程：

```
Buyer Query
    ↓
Intent & Entity Detection (COSMO Semantic Layer)
    ↓
Generated Answer
    ↓
Answer-to-Product Matching
├── Product Q&A Search
├── Specs & Description
└── Reviews Mining
    ↓
Feature Extraction Layer
提取实体、属性、意图
示例: "heater", "waterproof", "for kids", "1500W"
    ↓
Weighted Scoring Model
Final Score = α×SemanticSimilarity + β×AttributeOverlap + γ×IntentMatch + δ×COSMO-KG
    ↓
Reranking Layer
├── Session-based personalization
├── Popularity bias correction
└── Novelty/diversity balancing
    ↓
Top-N Product Recommendations
    ↓
Feedback Loop → COSMO → Retraining Data
```

### 加权评分公式

```
Final Score = α × SemanticSimilarity 
            + β × AttributeOverlap 
            + γ × IntentMatch 
            + δ × COSMO-KG relation score
```

**参数说明：**
- **α (Semantic Similarity)**：语义相似度（embedding 匹配）
- **β (Attribute Overlap)**：属性重叠度
- **γ (Intent Match)**：意图匹配度
- **δ (COSMO-KG relations)**：知识图谱关系得分

### 对 Listing 的启示

| 匹配维度 | Listing 优化建议 |
|----------|------------------|
| **Semantic Similarity** | 使用语义丰富的描述，避免重复 |
| **Attribute Overlap** | 完整填写产品属性，使用标准属性名 |
| **Intent Match** | Bullet Points 覆盖用户意图（用途、场景、人群） |
| **COSMO-KG relations** | 描述产品与常见用途的关系（"用于..."、"适合..."） |

### 重排序因素

| 因素 | 说明 |
|------|------|
| **Session-based personalization** | RUFUS 会根据用户会话历史个性化推荐 |
| **Popularity bias correction** | 热门产品不一定更适合，需要纠正偏差 |
| **Novelty/diversity balancing** | 结果需要多样性和新颖性 |

---

## 参考文献

- Yu et al. (2024). COSMO: A Large-Scale E-commerce Common Sense Knowledge Generation and Serving System at Amazon. SIGMOD 2024.
- Yu et al. (2022). FolkScope: Intention Knowledge Graph Construction for E-commerce.
