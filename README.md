# 🛍️ Boost sales through Promotional Campaigns with Product Pair Analysis
Promotional gifts aren't as simple as they seem. Behind every gift lies a complex balance of inventory availability, suppliers' conditions, and the cost-to-gain ratio. To maximize the effectiveness of promotional campaigns, one of common approaches I propose is that using product pair analysis.

The core idea is simple:
> **When a customer buys Product A, they often also have the tendency to buy Product B.**

This recurring behavior creates **product pairs**. The more frequent the pattern, the stronger the pair's potential to drive cross-sales.

---

## 🛠️ Tools & Tech

- **Excel** – With a raw Excel export of Sendo order details, I first cleaned the data, removing Cancelled orders/Gift items automatically added to carts (This ensured the analysis focused on true customer purchase behavior)
- **SQL** – For querying, joining, and aggregating transaction data
```sql
SELECT S1.sku, S2.sku, COUNT(DISTINCT S1.customer_tel) AS demand
FROM sendo_order S1
JOIN sendo_order S2
  ON S1.customer_tel = S2.customer_tel
  AND S1.sku < S2.sku
GROUP BY S1.sku, S2.sku
ORDER BY demand DESC;
```
- **Result**: The query returned 2,175 unique product pairs, sorted by descending demand (>50). To simplify presentation and gain a strategic overview, I visualized the output in Excel then grouped product pairs by category for higher-level analysis

---

## 🎯 Successful campaigns backed by this analysis: 
### 1. Beer & Instant Noodles Campaign:

- Scenario: A supplier offered us **1,000 cans of BIA VIỆT beer** for free. The challenge is how to distribute them effectively to **maximize sales impact**.
- Insight from Data: Through SQL analysis of customer purchasing patterns, we identified that **beer most frequently paired with instant noodles (mì, bún, phở ăn liền)** — with a strong demand count of **147**.
- Execution: We launched a campaign offering **1 free beer can** for any purchase over **50K VND** from the _instant noodles_ category.
- Result: The gifts **ran out within just 4 hours** after launch — proving that the pairing strategy drove **significant sales uplift**.

### 2. Meat & Vegetable Pairing Campaign: 
- ❓ Insight: Guess what customers typically buy after purchasing **meat**?
  You might think it's eggs, fruit or more meat, but data says otherwise.
- 💡 The top complementary category was **“Rau ăn củ”** (root/stem vegetables) — particularly **bí đao (wax gourd), bí đỏ (pumpkin), cà rốt (carrot), and dưa leo (cucumber)**. These four items consistently appeared in purchasing patterns following meat orders.
- Execution: Using this insight, we launched a **promotional combo** campaign that encouraged customers to buy both meat and selected vegetables together.
- 🚀 Result: The campaign drove **a noticeable uplift in cross-category sales**.

---
## 🎯 Other applications

Businesses can also use this analysis to:

- 🔍 **Highlight complementary products** visually on the product page
- 💬 **Trigger smart pop-up suggestions** or carousel recommendations

---
