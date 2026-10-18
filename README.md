# Power BI Advanced DAX: Category Performance & Filter Contexts

## 📌 Project Overview
This repository contains solutions for Codebasics exercises focusing on advanced DAX functions, matrix calculations, and custom filter context manipulations in Power BI.

## 📊 Visualizations Built
1. **Matrix Visualization (% Contribution to Total Sales):**
   * Calculates each category's relative performance against overall sales.
   * Uses `ALL` and `CALCULATE` to ensure the denominator (total sales) remains fixed even when category or brand filters are applied.
2. **Card Visualization (Category-Specific Filtered Sales):**
   * Designed to respond *only* to category-specific selections while ignoring all other report-level filters (like date, region, or brand) using `REMOVEFILTERS` and `KEEPFILTERS`.

## ⚙️ DAX Measures Used

### 1. Unfiltered Total Sales (Denominator for Matrix)
```dax
Overall Sales (Unfiltered) = 
CALCULATE(
    SUM(sales[sale_amount]),
    ALL(products[category], products[brand])
    )
```

### 2. Category-Specific Filtered Sales (Card Visual)
```dax
Category Filtered Sales = 
CALCULATE(
    SUM(sales[sale_amount]),
    REMOVEFILTERS(),
    KEEPFILTERS(sales[category])
)
```
