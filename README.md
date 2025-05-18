# 🛍️ Boost sales through Promotional Campaigns with Product Pair Analysis
Promotional gifts aren't as simple as they seem. Behind every gift lies a complex balance of inventory availability, suppliers' conditions, and the cost-to-gain ratio. To maximize the effectiveness of promotional campaigns, one of common approaches I propose is that using product pair analysis.

The core idea is simple:
> **When a customer buys Product A, they often also have the tendency to buy Product B.**

This recurring behavior creates **product pairs**. The more frequent the pattern, the stronger the pair's potential to drive cross-sales.

---

## 🛠️ Tools & Tech

- **Excel** – With a raw Excel export of Sendo order details, I first clean the data, removing Cancelled orders/Gift items automatically added to carts (This ensured the analysis focused on true customer purchase behavior)
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
- **Result**: The query returned 2,175 unique product pairs, sorted by descending demand (>50). Each row indicates how many unique customers bought both products together.
Results were exported to Excel for easier analysis, filtering, and presentation.

---

## 🎯 Applications

Businesses can use this analysis to:

- 🔍 **Highlight complementary products** visually on the product page
- 💬 **Trigger smart pop-up suggestions** or carousel recommendations
- 🎁 **Bundle products into combos** to boost average order value
- 💸 **Offer discounts** on Product B when Product A is purchased 

---
