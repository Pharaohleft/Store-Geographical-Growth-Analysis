# Study Overview and Data Context

**Austin Abraham**

**Date:** 10 Jan 2026

---

## Introduction

The purpose of this section is to integrate findings from three independent analytical artifacts—Offline US, Online US (E-commerce), and Europe—into a single, coherent view of performance.  
These datasets are not reconciled at the row level and are intentionally analyzed independently. The synthesis therefore focuses on pattern alignment, contrast, and structural differences, rather than numerical consolidation.

This project analyzes the same retail business across three independent contexts: Offline US, Online US, and Europe.  
I intentionally treated them as separate analytical systems, not a single reconciled dataset, because each channel has different economics and performance constraints.

Offline US was a deep diagnostic analysis focused on category and sub-category profitability. That’s where I found significant margin dispersion — including high-revenue products that were structurally unprofitable.

Online US was a KPI- and YoY-driven analysis. What stood out there was that volume was declining, but profit and margin were improving, indicating efficiency or pricing gains rather than demand growth.

Europe was analyzed through a target-based lens across multiple years. Sales and profit grew every year, but target over-achievement declined, which suggests execution pressure rather than underperformance.

The synthesis was the most important part. Across all three, Consumer demand consistently anchors performance, geography is highly concentrated, and fulfillment strategies are standardized.

The key takeaway is that scale, efficiency, and execution discipline behave differently across channels, so performance management has to be channel-specific rather than driven by global averages.

---

Super Store is a small retail business located in the United States. They sell Furniture, Office Supplies and Technology products and their customers are the mass Consumer, Corporate and Home Offices. The data set contains sales, profit and geographical information of individual orders.

Our task is to determine weak areas and opportunities for Super Store to boost business growth.

---

## Business Questions

- Which Category is Best Selling and Most Profitable?
- What are the Best Selling and Most Profitable Sub-Category?
- Which is the Top Selling Sub-Category?
- Which Customer Segment is Most Profitable?
- Which is the Preferred Ship Mode?
- Which Region is the Most Profitable?
- Which City has the Highest Number of Sales?

---

## Who is Reading this Analysis?

- Assuming that the Super Store is a family business and is owned by 1 or 2 owners who are very invested in their business.
- Owners are likely not people who are expert in reading charts or interpreting statistical analysis, so our analysis will be in layman terms and easy to understand.
- They needs information to make informed decisions on how to boost business profit so, our analysis focus on finding weaknesses or opportunities and providing recommendations and marketing strategies.

---

## Preparing the Environment

We will import the required libraries and read in the data set.

- Pandas - Data manipulation
- Matplotlib and Seaborn - Data visualisation

---

## Scope, assumptions, and analytical standards (portfolio addendum)

**Dataset:** Sample Superstore (US retail, offline order-line transactions)  
**Grain:** Each row is an *order line* (one product line within an order), not a full order.

- This is **descriptive / diagnostic analytics** (performance, mix, and profitability patterns).
- It does **not** attempt row-level reconciliation with other channels (online US, online EU).
- It does **not** claim causal effects (e.g., ship mode *causes* profit changes) without experimentation.

### Data hygiene checks added
- Explicit datetime parsing for order and ship dates
- Missing-value and duplicate checks (order-line vs order)
- Derived metrics: shipping days, profit margin (weighted when aggregated)

---

## Questions Answered 

| Business Question | Evidence Section |
|------------------|-----------------|
| Which categories drive profit? | Section 2.1 |
| Which sub-categories generate losses? | Section 2.2 |
| Which customer segments matter most? | Section 2.3 |
| Where is profit geographically concentrated? | |

### Product Performance
- How do sales and profit vary across product categories and sub-categories?
- Are losses concentrated in specific sub-categories?

### Geographic Performance
- How does offline performance differ across regions and cities?
- Do high-sales geographies also exhibit high profitability?

### Fulfillment Behavior
- How do different shipping modes compare in terms of sales volume, profitability, and delivery speed?

### Discounting and Profitability
- How does discount intensity relate to profit and profit margin?
- Are higher discounts systematically associated with margin erosion?

---

## Business Context

This report analyzes offline retail transaction data from a U.S.-based multi-category retailer to quantify how sales, profit, and margin vary across products, customer segments, and geographies.

The dataset contains 9,994 order-line records with no missing values, enabling complete aggregation across all dimensions analyzed.

## Observed Dataset Size (from notebook output)

- **9,994 rows and 13 fields** (DataFrame shape: (9994, 13))
- **0 missing values across all columns** (null-count output shows 0 for every column)

---

## Business Outcomes Captured

- **Total Sales:** $2,296,195.59
- **Total Profit:** $286,241.42
- **Total Quantity:** 37,820 units
- **Overall weighted profit margin:** 12.47% (Profit ÷ Sales)
### Category economics
Which categories drive sales vs profit, and where does margin structurally underperform?

### Sub-category drivers
Which sub-categories are top revenue drivers, and which are profit engines vs profit leaks?

### Customer mix
Which customer segments contribute the most profit?

### Regional profitability
How is profit distributed across regions?
<img width="602" height="331" alt="Picture1" src="https://github.com/user-attachments/assets/2616b3fb-5115-4150-8a8b-10053fe92a48" />
### Result 1 — Profitability is highly uneven by category

From the category summary table (Sales, Profit, and weighted margin):

- **Technology:** Sales $836,154.03, Profit $145,454.95, 17.40% weighted margin
- **Office Supplies:** Sales $718,735.24, Profit $122,364.66, 17.03% weighted margin
- **Furniture:** Sales $741,306.31, Profit $18,421.81, 2.49% weighted margin

**Interpretation (strictly from the results):**

Furniture generates ~32.3% of sales (741,306 / 2,296,196) but only ~6.4% of total profit (18,422 / 286,241).
Furniture has a weighted profit margin of 2.49%, compared to 17.40% for Technology and 17.03% for Office Supplies.
Technology + Office Supplies are the profit backbone (combined profit $267,819.61, ~93.6% of total profit).
<img width="602" height="288" alt="Picture2" src="https://github.com/user-attachments/assets/8a29abbc-4e4d-48cb-b214-7640ee9b0aa3" />

### Top sub-categories by Sales (examples from table)

- **Phones:** Sales $330,007.05, Profit $44,515.73, 13.49% margin
- **Chairs:** Sales $327,777.76, Profit $26,567.13, 8.11% margin
- **Storage:** Sales $223,843.61, Profit $21,278.83, 9.51% margin

### Top sub-category by Profit

- **Copiers:** Profit $55,617.82 on Sales $149,528.03 → 37.20% margin

### Largest explicit loss sub-category shown

- **Tables:** Sales $206,965.53, Profit –$17,725.48, –8.56% margin


**Interpretation (strictly from results):**

The portfolio contains at least one high-revenue segment (“Tables”) that is structurally unprofitable at the aggregate level (negative total profit and negative weighted margin).

Profit leadership is not tied to sales leadership: Copiers is a profit engine despite lower sales than Phones/Chairs.
<img width="574" height="609" alt="Picture3" src="https://github.com/user-attachments/assets/6f8028ce-3a7a-4c6f-a96d-d78466ebb2f3" />

---
<img width="602" height="378" alt="Picture4" src="https://github.com/user-attachments/assets/d68e221a-48f2-4bff-95a8-c8e448aac492" />

- **Consumer:** $134,007.44 profit
- **Corporate:** $91,954.98 profit
- **Home Office:** $60,279.00 profit

As shares of total profit ($286,241.42):

- **Consumer:** ≈ 46.8%
- **Corporate:** ≈ 32.1%
- **Home Office:** ≈ 21.1%

## Category Summary Metrics

### Total Sales by Category
- **Technology:** $836,154.03 (36.41%)
- **Furniture:** $741,306.31 (32.28%)
- **Office Supplies:** $718,735.24 (31.30%)

---

### Total Profit by Category
- **Technology:** $145,454.95 (50.82%)
- **Office Supplies:** $122,364.66 (42.75%)
- **Furniture:** $18,421.81 (6.44%)

---

### Weighted Profit Margin by Category
- **Technology:** 17.40%
- **Office Supplies:** 17.03%
- **Furniture:** 2.49%

---

### Total Quantity by Category
- **Office Supplies:** 22,861 units (60.45%)
- **Furniture:** 8,020 units (21.21%)
- **Technology:** 6,939 units (18.35%)

## Sub-Category Summary Metrics

### Top Sub-Categories by Sales
- **Phones:** $330,007.05 sales, $44,515.73 profit, 13.49% margin
- **Chairs:** $327,777.76 sales, $26,567.13 profit, 8.11% margin
- **Storage:** $223,843.61 sales, $21,278.83 profit, 9.51% margin
- **Tables:** $206,965.53 sales, –$17,725.48 profit, –8.56% margin

---

### Top Sub-Categories by Profit
- **Copiers:** $55,617.82 profit on $149,528.03 sales (37.20% margin)
- **Phones:** $44,515.73 profit on $330,007.05 sales (13.49% margin)

---

### Loss-Making Sub-Categories
- **Tables:** –$17,725.48 total profit (–8.56% margin)

---

### Margin Dispersion Examples

**Technology sub-categories:**
- **Copiers:** 37.20%
- **Phones:** 13.49%

**Furniture sub-categories:**
- **Chairs:** 8.11%
- **Tables:** –8.56%

- **Which categories generate the most sales?**  
  Technology leads sales (36.41%), followed by Furniture (32.28%) and Office Supplies (31.30%).

- **Which categories generate the most profit?**  
  Technology (50.82%) and Office Supplies (42.75%) account for 93.6% of total profit.

- **Which categories have the highest and lowest margins?**  
  Technology (17.40%) and Office Supplies (17.03%) are highest; Furniture is lowest (2.49%).

- **Which sub-categories drive revenue?**  
  Phones, Chairs, Storage, and Tables are top revenue sub-categories.

- **Which sub-categories drive profit?**  
  Copiers and Phones are the top profit contributors.

- **Are there loss-making sub-categories?**  
  Tables shows negative total profit (–$17,725.48).

- **Which customer segments contribute the most profit?**  
  Consumer contributes the most profit (46.8%), followed by Corporate (32.1%) and Home Office (21.1%).

- **How is profit distributed geographically?**  
  West (38%) and East (32%) together account for 70% of profit.


<img width="465" height="402" alt="Picture5" src="https://github.com/user-attachments/assets/39fed3c4-e0d2-4dd0-8dd0-57715c81cbec" />

-West: 38% of profit
-East: 32% of profit
-South: 16% of profit
-Central: 14% of profit
The West + East regions together account for 70% of total offline profit, leaving the South and Central regions to share the remaining 30%.
A small number of cities dominate sales and unit volume, while the majority of cities contribute relatively modest amounts.

The distribution is long-tailed, with top cities acting as volume anchors.
### Sales leadership: Technology is #1; categories are otherwise close in revenue

**Category Sales totals:**

- **Technology:** $836,154.03 (36.41% of total sales)
- **Furniture:** $741,306.31 (32.28%)
- **Office Supplies:** $718,735.24 (31.30%)

**What this means (purely from results):**  
Sales are relatively balanced across the three categories (each ~31–36% of revenue), so profitability differences are not driven purely by “one category being tiny.”

---

### Result 2 — Profit leadership is concentrated in Technology + Office Supplies

**Category Profit totals:**

- **Technology:** $145,454.95 (50.82% of total profit)
- **Office Supplies:** $122,364.66 (42.75%)
- **Furniture:** $18,421.81 (6.44%)

**Concentration statement (directly computed from table totals):**  
Technology + Office Supplies contribute ~93.6% of total profit ($267,819.61 of $286,241.42) while representing ~67.7% of sales.

---

### Result 3 — Furniture is the margin outlier (structurally low weighted margin)

**Weighted profit margins:**

- **Technology:** 17.40%
- **Office Supplies:** 17.03%
- **Furniture:** 2.49%

**Another way to state the gap:**

For every $1 of sales:

- Technology generates $0.174 profit
- Office Supplies generates $0.170 profit
- Furniture generates $0.025 profit

This is not a small difference — Furniture’s weighted margin is ~7× lower than the other categories.

---

### Result 4 — Unit volume is dominated by Office Supplies (quantity-heavy category)


- **Office Supplies:** 22,861 units (60.45% of all units sold)
- **Furniture:** 8,020 units (21.21%)
- **Technology:** 6,939 units (18.35%)

- Office Supplies is a high-volume, high-margin category (60% of units, ~17% margin).
- Technology is lower volume but highest profit (18% of units but ~51% of profit).
- Furniture is moderate volume, moderate sales, but weak profit conversion.

- **Furniture is the category-level profitability problem.**  
  It produces 32.28% of sales but only 6.44% of profit, with a 2.49% weighted margin. This combination signals a structural issue (pricing/discounting/product mix) rather than random noise.

- **Technology + Office Supplies are carrying profitability.**  
  Combined they generate ~93.6% of total profit. Any strategy that harms these categories (e.g., aggressive discounting) risks disproportionate profit impact.

- **Volume ≠ profit.**  
  Office Supplies sells 60% of units, but Technology generates the most profit. Portfolio decisions should therefore track both:
  - unit velocity (quantity)
  - economic yield (profit + weighted margin)

## Sub-category performance

Sub-category performance was evaluated by aggregating Sales, Profit, and Quantity at the Sub-Category level. Profitability was assessed using weighted profit margin (Total Profit ÷ Total Sales). Rankings were produced for:
- Top sub-categories by Sales
- Top sub-categories by Profit
- Loss-making sub-categories (negative total profit)

---

## Results

### Top sub-categories by Sales
- **Phones:** $330,007.05 sales, $44,515.73 profit, 13.49% margin
- **Chairs:** $327,777.76 sales, $26,567.13 profit, 8.11% margin
- **Storage:** $223,843.61 sales, $21,278.83 profit, 9.51% margin
- **Tables:** $206,965.53 sales, –$17,725.48 profit, –8.56% margin
- Three of the top four revenue-generating sub-categories have single-digit to low-teens margins.
- One of the top revenue drivers (Tables) is loss-making at the aggregate level.

---

### From the “Most Profitable Sub-Category” output
- **Copiers:** $55,617.82 profit on $149,528.03 sales → 37.20% weighted margin
- **Phones:** $44,515.73 profit on $330,007.05 sales → 13.49% margin
- Copiers generates more profit than Phones despite having ~45% of Phones’ sales.
- The profit margin for Copiers (37.20%) is nearly 3× that of Phones and ~15× that of Tables.

---

### From the loss-ranking output
- **Tables:** –$17,725.48 total profit (–8.56% margin)
- Other sub-categories (from the table) show positive but materially lower margins than category leaders.
- The largest absolute loss in the sub-category portfolio comes from a single sub-category with meaningful revenue.
- This indicates localized structural loss, not broad sub-category failure.

---

### Within-category contrasts

**Within the Technology category alone:**
- **Copiers:** 37.20% margin
- **Phones:** 13.49% margin

**Within Furniture:**
- **Chairs:** 8.11% margin
- **Tables:** –8.56% margin

- Sub-categories within the same category can differ by 40+ percentage points in margin.
- Category-level averages therefore mask risk and opportunity at the sub-category level.

---

### Implications

1. **Sub-category analysis is essential for profitability management.**  
   Category-level views would miss that:
   - Tables is a high-revenue but loss-making segment.
   - Copiers is a disproportionately strong profit engine.

2. **Revenue leadership does not imply economic health.**  
   Phones and Chairs are top sellers, but their margins are materially lower than best-in-class sub-categories.

3. **Profit leakage is concentrated and actionable.**  
   The largest losses originate from specific sub-categories, suggesting targeted interventions (pricing, discounting, assortment) rather than category-wide changes.

## Customer segment profitability

Customer performance was evaluated by aggregating Profit at the Segment level (Consumer, Corporate, Home Office). Results are reported as absolute profit and share of total profit to assess contribution concentration.

### From the segment profit output:
- **Consumer:** $134,007.44
- **Corporate:** $91,954.98
- **Home Office:** $60,279.00

### As shares of total profit ($286,241.42):
- **Consumer:** 46.8%
- **Corporate:** 32.1%
- **Home Office:** 21.1%

Nearly half of all offline profit comes from Consumer customers, with Corporate contributing roughly one-third, and Home Office the remaining one-fifth.

---

### Consumer > Corporate > Home Office:
- **Consumer generates $42,052.46 more profit than Corporate.**
- **Consumer generates $73,728.44 more profit than Home Office.**
- **Corporate generates $31,675.98 more profit than Home Office.**

This is not a marginal difference; it indicates structurally different profit contributions by segment.

---

## Category Economics

### Table 2.1 — Category Performance Summary

| Category | Sales ($) | Profit ($) | Quantity | Weighted Margin |
|--------|-----------|------------|----------|-----------------|
| Technology | 836,154 | 145,455 | 6,939 | 17.40% |
| Office Supplies | 718,735 | 122,365 | 22,861 | 17.03% |
| Furniture | 741,306 | 18,422 | 8,020 | 2.49% |

---

### Figure 2.1 — Sales, Profit, and Quantity by Category
*(Insert 3-panel bar chart from notebook)*

---

## 2.2 Sub-Category Performance

### Table 2.2 — Selected Sub-Category Results

| Sub-Category | Sales ($) | Profit ($) | Margin |
|-------------|-----------|------------|--------|
| Phones | 330,007 | 44,516 | 13.49% |
| Chairs | 327,778 | 26,567 | 8.11% |
| Storage | 223,844 | 21,279 | 9.51% |
| Copiers | 149,528 | 55,618 | 37.20% |
| Tables | 206,966 | –17,725 | –8.56% |

---

### Figure 2.2 — Best Selling vs Most Profitable Sub-Categories

---

## 2.3 Customer Segment Profitability

### Table 2.3 — Profit by Customer Segment

| Segment | Profit ($) | Share of Total |
|--------|------------|----------------|
| Consumer | 134,007 | 46.8% |
| Corporate | 91,955 | 32.1% |
| Home Office | 60,279 | 21.1% |


## Conclusions

1. **Consumer customers are the primary profit engine of offline sales.**  
   With 46.8% of total profit, the Consumer segment is the single largest contributor to profitability in the offline channel.

2. **Corporate is a strong secondary contributor, not a niche segment.**  
   At 32.1% of profit, Corporate materially impacts overall profitability and should be managed as a core segment, not a support segment.

3. **Home Office is meaningfully smaller in profit impact.**  
   While profitable, Home Office contributes less than half the profit of Consumer and should be evaluated with segment-appropriate expectations.
## Key Findings (Results Only)

### 1. Profitability is highly concentrated by category

Technology and Office Supplies together generate 93.6% of total profit while accounting for 67.7% of sales.

Furniture generates 32.3% of sales but only 6.4% of profit, with a 2.49% weighted margin versus ~17% for the other two categories.

---

### 2. Sub-category performance diverges sharply from category averages

Top revenue sub-categories:
- Phones ($330K)
- Chairs ($328K)
- Storage ($224K)
- Tables ($207K)

Top profit sub-category:
- Copiers — $55.6K profit on $149.5K sales (37.2% margin).

Largest loss sub-category:
- Tables — –$17.7K profit, –8.56% margin, despite being a top-4 revenue driver.

Margin dispersion within the same category exceeds 40 percentage points (e.g., Copiers vs Tables).

---

### 3. Profit contribution varies materially by customer segment

- Consumer: $134.0K profit (46.8% of total)
- Corporate: $92.0K profit (32.1%)
- Home Office: $60.3K profit (21.1%)

Profit contribution declines monotonically from Consumer → Corporate → Home Office.

---

### 4. Geographic profit is not evenly distributed

West (38%) and East (32%) regions together generate 70% of total offline profit.

South (16%) and Central (14%) account for the remaining 30%.

City-level outputs show sales and unit volume are highly concentrated, but profit concentration is even stronger at the regional level.
## Key Performance Indicators (KPIs)

The following KPIs summarize offline store performance at an aggregate level and frame the results that follow:

- **Total Sales:** $2.30M
- **Total Profit:** $286.2K
- **Overall Weighted Profit Margin:** 12.47%
- **Total Units Sold:** 37,820
- **Number of Transactions (Order Lines):** 9,994

---

## Category-Level KPIs

- **Highest Sales Category:** Technology ($836.2K, 36.4% of sales)
- **Highest Profit Category:** Technology ($145.5K, 50.8% of profit)
- **Lowest Margin Category:** Furniture (2.49% weighted margin)

---

## Sub-Category KPIs

- **Top Revenue Sub-Category:** Phones ($330.0K sales)
- **Top Profit Sub-Category:** Copiers ($55.6K profit, 37.2% margin)
- **Largest Loss Sub-Category:** Tables (–$17.7K profit, –8.56% margin)

---

## Customer & Geography KPIs

- **Top Profit Segment:** Consumer (46.8% of total profit)
- **Top Profit Region:** West (38% of total profit)
- **Profit Concentration:** West + East = 70% of total profit
<img width="1292" height="721" alt="6" src="https://github.com/user-attachments/assets/d999b221-8a0d-4d8f-b744-613ab951dda5" />
•	Office Supplies has the highest YTD Sales in absolute terms.
•	Furniture is the only category with positive YoY growth.
•	Technology and Office Supplies both show YoY declines.
<img width="1296" height="724" alt="7" src="https://github.com/user-attachments/assets/4fdcfb49-5720-4427-9b66-3a8f6734f8d5" />


1.	Office Supplies is the largest revenue category for Consumer.
2.	Furniture is the only category with positive YoY growth.
3.	Technology shows the largest YoY decline among Consumer categories.
<img width="1287" height="726" alt="8" src="https://github.com/user-attachments/assets/b7d63bf2-8e54-4eec-9b6f-c15b3b4b4f2f" />

•	Office Supplies is the largest revenue category for Corporate.
•	All three categories show negative YoY growth.
•	Furniture shows the largest YoY decline among Corporate categories.
<img width="1297" height="722" alt="9" src="https://github.com/user-attachments/assets/94cad6ab-3588-47d9-9c4e-e48f3ea44f2b" />
Office Supplies is the largest revenue category for Home Office.	Technology and Furniture both show positive YoY growth.	Office Supplies shows a YoY decline.

## Segment Comparison — Results Only

*(All values taken directly from the dashboard screenshots; percentages are arithmetic shares vs baseline. No interpretation.)*

---

### Segment KPI Comparison (YTD)

| Segment | YTD Sales | Share of Sales | YTD Profit | Share of Profit | YTD Quantity | Share of Qty | Profit Margin | YoY Sales | YoY Profit | YoY Qty | YoY Margin |
|-------|-----------|----------------|------------|-----------------|--------------|--------------|---------------|-----------|------------|---------|------------|
| All Segments | $11.53M | 100% | $1.34M | 100% | 107.2K | 100% | 11.58% | –0.83% | +4.50% | –7.29% | +5.37% |
| Consumer | $5.98M | ~51.9% | $0.71M | ~53.0% | 55.4K | ~51.7% | 11.92% | –0.55% | +8.04% | –6.57% | +8.63% |
| Corporate | $3.50M | ~30.4% | $0.39M | ~29.1% | 32.9K | ~30.7% | 11.12% | –0.66% | –2.95% | –6.55% | –2.31% |
| Home Office | $2.06M | ~17.9% | $0.23M | ~17.2% | 18.9K | ~17.6% | 11.35% | –1.93% | +7.49% | –10.54% | +9.60% |

---

### Category YoY by Segment (Results Only)

| Segment | Technology YoY | Furniture YoY | Office Supplies YoY |
|-------|----------------|---------------|---------------------|
| Consumer | –2.46% | +1.42% | –0.67% |
| Corporate | –1.13% | –1.80% | –0.08% |
| Home Office | +1.20% | +3.23% | –4.67% |

---

### Regional Sales Share by Segment (YTD %)

| Segment | West | East | Central | South |
|-------|------|------|---------|-------|
| All Segments | 32.22% | 28.42% | 23.19% | 16.17% |
| Consumer | 32.07% | 28.38% | 23.29% | 16.25% |
| Corporate | 32.76% | 27.94% | 22.95% | 16.35% |
| Home Office | 31.73% | 29.34% | 23.28% | 15.65% |

---

### Shipping Mix by Segment (YTD %)

| Segment | Standard | Second | First | Same Day |
|-------|----------|--------|-------|----------|
| All Segments | 60.51% | 19.22% | 15.10% | 5.17% |
| Consumer | 59.98% | 19.50% | 15.17% | 5.36% |
| Corporate | 61.18% | 19.12% | 14.71% | — |
| Home Office | 60.90% | 18.59% | 15.57% | 4.94% |

---

## B. Executive Summary — Dashboard #1 (US E-commerce)

### Purpose

This dashboard evaluates US e-commerce performance using YTD KPIs and YoY growth to understand how sales, profit, volume, and margin vary by customer segment, category, region, product, and shipping type. The analysis is structured around a front-loaded set of questions (listed next in the report) and presents results first, with interpretation separated.

---

### Data & KPIs (Baseline)

- **YTD Sales:** $11.53M (YoY –0.83%)
- **YTD Profit:** $1.34M (YoY +4.50%)
- **YTD Quantity:** 107.2K (YoY –7.29%)
- **YTD Profit Margin:** 11.58% (YoY +5.37%)

---

### Summary of Results (Preview)

- Sales are slightly down YoY, while profit and margin are up at the aggregate level.
- Consumer represents the largest share of sales (~52%), profit (~53%), and quantity (~52%), with positive YoY profit and margin.
- Corporate shows negative YoY profit and margin despite stable sales share (~30%).
- Home Office shows positive YoY profit and margin with the largest YoY quantity decline.
- Across all segments, Office Supplies is the largest revenue category; regional mix is stable (West/East dominant); Standard Class accounts for ~60% of shipping.

Readers should proceed to the Questions Answered section to assess relevance, then scroll to the Analysis for evidence.

---

## C. Business Implications — Dashboard #1

*(Interpretation begins here; grounded strictly in the results above.)*

- Profit resilience is segment-dependent.  
  Aggregate profit growth is supported primarily by Consumer and Home Office, while Corporate shows YoY declines in profit and margin.

- Volume contraction coexists with margin expansion.  
  All segments show YoY quantity declines, yet margin improves for Consumer and Home Office, indicating changes in mix or pricing effectiveness rather than volume recovery.

- Category strategies should be segment-specific.  
  Furniture grows YoY in Consumer and Home Office but declines in Corporate; Office Supplies declines YoY in all segments, most sharply in Home Office.

- Geographic allocation is stable; optimization likely lies elsewhere.  
  Regional sales shares are consistent across segments, suggesting limited upside from regional reallocation versus segment/category actions.

- Shipping mix is standardized across segments.  
  With ~60% Standard Class across all segments, improvements in service or cost would have system-wide impact rather than segment-specific effects.
## Questions Answered

*(US E-commerce Performance Dashboard)*

This dashboard and analysis are designed to answer the following questions about U.S. e-commerce performance:

- How is overall e-commerce performance trending year-to-date in terms of sales, profit, quantity sold, and profit margin?

- Is year-over-year growth consistent across sales, profit, volume, and margin, or are these metrics diverging?

- Which customer segments contribute the most to e-commerce sales and profit?

- How do sales, profit, and margin trends differ between Consumer, Corporate, and Home Office segments?

- Are declines or improvements in performance driven more by volume changes or margin changes?

- How does year-to-date sales performance vary across product categories within each customer segment?
<img width="1273" height="707" alt="10" src="https://github.com/user-attachments/assets/911b5e26-6c48-4c99-bd5a-41eb3e2f1b95" />
## Summary of Results (Preview)

- Sales and profit increase monotonically by year from 2021 → 2023, with 2023 delivering the highest absolute sales (630K) and profit (77K).

- Target achievement is strongest in earlier years (2021: 115.3%) and declines through 2023 (105.7%), despite higher absolute sales.

- Central Europe consistently dominates sales, contributing 54–59% across all years.

- Consumer remains the largest customer segment every year, followed by Corporate, then Home Office.

- Economy shipping is the primary fulfillment mode across all years, accounting for the majority of sales volume.

- Sales are highly concentrated in a small set of countries, led by France, Germany, and the United Kingdom.

Detailed evidence supporting these points appears in the Analysis and Year Comparison sections.

---

## How to Read This Report

- Use the Questions Answered section to assess relevance.
- Review Year Comparison (Results Only) to see how performance shifts over time.
- Refer to Business Implications for interpretation and strategic takeaways.

---

## C. Business Implications — Dashboard #2 (Europe)

*(Interpretation begins here; grounded strictly in observed results.)*

- **Target attainment is weakening despite sales growth.**  
  While total sales and profit rise year over year, target achievement declines from 115.3% (2021) to 105.7% (2023), indicating that targets are increasing faster than realized performance.

- **Growth is scale-driven, not efficiency-driven.**  
  Higher absolute sales in later years do not translate into proportionally higher target over-achievement, suggesting that improvements are coming from scale expansion rather than improved execution against goals.

- **European sales are structurally concentrated.**  
  Central Europe consistently contributes over half of total sales, and three countries (France, Germany, UK) dominate year after year. This concentration increases exposure to regional and country-specific risks.

- **Customer mix remains stable over time.**  
  Consumer sales lead in every year, with Corporate and Home Office maintaining consistent rank order. Major year-to-year performance changes are therefore unlikely to be driven by segment mix shifts alone.

- **Shipping strategy is standardized and system-wide.**  
  Economy shipping dominates across all years, indicating that logistics optimization or disruption would have broad, cross-year impact, rather than being isolated to specific periods.

- **Performance volatility is temporal, not structural.**  
  Monthly peaks consistently occur in the second half of the year, implying seasonality effects that recur regardless of total annual performance.
Offline US is a scale-heavy business with localized profit leakage, driven by product-level margin dispersion.

Online US demonstrates profit resilience amid declining volume, indicating improved monetization rather than demand growth.

Europe shows consistent target over-achievement, but with declining efficiency over time as targets rise faster than realized sales.

Taken together, these analyses indicate that performance optimization requires channel-specific strategies, not global averages or one-size-fits-all interventions.

---

## Recommendations (Strategic, Not Tactical)

- **Shift performance management from category-level to sub-category-level control (Offline US).**  
  High-revenue loss pockets coexist with high-margin sub-categories. Without sub-category governance, aggregate performance metrics will mask profit erosion.

- **Protect margin gains in Online US while addressing volume contraction.**  
  The divergence between declining quantity and rising profit margin suggests pricing or mix improvements that should be preserved while selectively targeting volume recovery.

- **Recalibrate target-setting discipline in Europe.**  
  Persistent over-achievement alongside declining target attainment percentages suggests targets may be escalating faster than operational capacity or demand growth.

- **Treat geography as a risk concentration variable, not just a growth lever.**  
  All three analyses reveal heavy geographic concentration. Performance shocks in a small number of regions or countries would have outsized impact.

- **Recognize fulfillment strategy as a system-wide lever.**  
  Dominance of a single shipping mode across channels means logistics changes—positive or negative—will propagate broadly rather than locally.
