
# 📊 DAX Measures

This document contains the DAX measures used in the **Customer Sales Analytics Dashboard** built in Power BI.

---

# 💰 Sales Measures

## Total Sales

```DAX
Total Sales = SUM(fact_sales[cost])
```

Calculates the total sales generated.

---

## Total Orders

```DAX
Total Orders = DISTINCTCOUNT(fact_sales[line_id])
```

Returns the total number of orders.

---

## Total Customers

```DAX
Total_customers = DISTINCTCOUNT(dim_customer[customer_id])
```

Returns the number of unique customers.

---

## Average Revenue per Customer

```DAX
Average Revenue per Customer = DIVIDE([Total Sales],[Total Customers])
```

Calculates the average revenue generated per customer.

---

## Average Orders per Customer

```DAX
Average Orders per Customer = DIVIDE([Total Orders],[Total Customers])

```

Calculates the average number of orders placed by each customer.

---

## Average Order Value

```DAX
Average Order Value = DIVIDE([Total Sales],[Total Orders])
```

Calculates the average value of an order.

---

## Total Discount

```DAX
Total Discount = SUM(fact_sales[discount])
```

Calculates the total discount offered.

---

## Active Regions

```DAX
Active Regions = DISTINCTCOUNT(dim_geo[region])
```

Returns the total number of active regions.

---

# 📢 Campaign Measures

## Campaign Revenue

```DAX
Campaign Revenue = SUM(fact_sales[cost])
```

Total revenue generated from campaigns.

---

## Campaign Spend

```DAX
Campaign Spend = SUM(fact_campaign_spend[Spend])
```

Calculates the total campaign expenditure.

---

## ROI

```DAX
ROI = 
DIVIDE(
    [Campaign Revenue] - [Campaign Spend],
    [Campaign Spend],
    0
)
```

Calculates Return on Investment.

---

## CTR (Click Through Rate)

```DAX
CTR = 
DIVIDE(
    SUM(fact_campaign_spend[clicks]),
    SUM(fact_campaign_spend[impressions]),
    0
)
```

Calculates Click Through Rate.

---

## Total Campaigns

```DAX
Total Campaigns = DISTINCTCOUNT(dim_campaign[campaign_key])
```

Returns the total number of campaigns.

---

# 📦 Inventory Measures

## Total Inventory Units

```DAX
Total Inventory Units = SUM(fact_inventory[untis])
```

Returns the total inventory units available.

---

## Total Products

```DAX
Total Products = 
DISTINCTCOUNT(dim_product[product_key])
```

Returns the total number of products.

---

## Total Categories

```DAX
Total Categories = 
DISTINCTCOUNT(dim_product[category])
```

Returns the total number of product categories.

---

## Average Units/Product

```DAX
Average Units/Product = 
DIVIDE(
    [Total Inventory Units],
    [Total Products]
)
```

Calculates the average inventory units per product.

---

## Inventory Value

```DAX
Inventory Value = 
SUMX(
    fact_inventory,
    fact_inventory[untis] *
    RELATED(dim_product[price])
)
```

Calculates the total inventory value using product price and available units.

---

# 📝 Notes

- The project follows a **Star Schema** data model.
- All KPIs shown in the dashboards are powered by these DAX measures.
- Measures are organized into Sales, Campaign, and Inventory categories for better maintainability.

---

**Project:** Customer Sales Analytics Dashboard

**Tool:** Microsoft Power BI

**Language:** DAX (Data Analysis Expressions)

**Author:** Muskan Saini
