# Sales Dashboard (Power BI)

A one-page Power BI dashboard that shows sales, profit, quantity and profit margin for a product-selling business, with breakdowns by month, day, category, sale type and payment mode.

**Data period:** 1 January 2024 to 31 December 2025 · **527 transactions** · **45 products**

---

## Contents

| File | Description |
|---|---|
| `Sales_Dashboard.pbix` | The Power BI report (one page, 1920 × 1080) |
| `Sales-Dashboard-_Data.xlsx` | Source data with two sheets: `Input Data` and `Master Data` |
| `README.md` | This file |

---

## What the dashboard shows

**KPI cards**

- Total Sales (net sales after discount)
- Profit
- Profit %
- Quantity

**Charts**

| Chart | Type | Shows |
|---|---|---|
| Total Selling Price by Day | Area chart | Sales by day |
| Sales & Profit by Month | Column chart | Monthly sales and profit (Profit % in tooltip) |
| Sales by Category | Clustered bar | Sales ranking by category |
| Sales by Product | Treemap | Sales share (currently grouped by category) |
| Sales by Type | Donut | Direct Sales, Online and Wholesaler share |
| Sales by Payment Mode | Donut | Cash and Online share |

**Filters (slicers):** Month, Year, Payment Mode, Sale Type. They filter every visual on the page.

---

## Data

**Input Data** (one row per sale)

| Column | Description |
|---|---|
| `DATE` | Date of the sale |
| `PRODUCT ID` | Product code (links to Master Data) |
| `QUANTITY` | Units sold |
| `SALE TYPE` | Direct Sales, Online or Wholesaler |
| `PAYMENT MODE` | Cash or Online |
| `DISCOUNT %` | Discount on the list price (2% to 15%) |

**Master Data** (one row per product)

| Column | Description |
|---|---|
| `PRODUCT ID` | Unique product code |
| `PRODUCT` | Product name |
| `CATEGORY` | Product group |
| `UOM` | Unit of measure (Kg, Lt, Ft, No.) |
| `BUYING PRIZE` | Cost price per unit |
| `SELLING PRICE` | List price per unit |

---

## How the numbers are calculated

The Excel file has no price or total columns, so the values are derived as follows (reconstructed from the data; check them against the measures in the `.pbix` file):

```
Net sales (Total Selling Price) = QUANTITY × SELLING PRICE × (1 − DISCOUNT %)
Cost                            = QUANTITY × BUYING PRIZE
Profit                          = Net sales − Cost
Profit %                        = Profit ÷ Net sales
```

---

## Headline results

| Measure | Value |
|---|---|
| Net sales | 366,618 |
| Profit | 34,114 (9.3% margin) |
| Discounts given | 34,794 (8.7% of sales at list price) |
| Loss-making transactions | 106 of 527 (20%) |
| Net sales growth, 2024 to 2025 | +14.9% |
| Profit growth, 2024 to 2025 | +49.6% |

**Main findings**

- Discounts remove about half of the profit that would otherwise be earned.
- The 15% discount is the most used, and earns only a 1.9% margin.
- Seven products lose money overall, because the discount exceeds their list margin.
- The top 10 products give 44.5% of sales but 76.7% of profit.

---

## Known issues

- The treemap titled "Sales by Product" is grouped by category, not product.
- Many products are in the wrong category in Master Data, and Sugar's unit is recorded as "Ft".
- The daily chart is sorted by value, not by date.
- There is no Date table, so month order and year-on-year comparison are not reliable.
- The Quantity card adds Kg, Lt, Ft and pieces together.
- Profit appears in only one chart; there is no discount view.
- No mobile layout, no alt text, and no "last refreshed" date.

The full list, with severity and recommended fixes, is in the project documentation.

---

## Getting started

**Requirements:** Power BI Desktop (current version).

1. Download `Sales_Dashboard.pbix` and `Sales-Dashboard-_Data.xlsx` into the same folder.
2. Open `Sales_Dashboard.pbix` in Power BI Desktop.
3. If asked, point the data source to your copy of `Sales-Dashboard-_Data.xlsx`
   (Home > Transform data > Data source settings > Change Source).
4. Select **Refresh** on the Home tab to load the latest data.

---

## Updating the data

1. Add new sales rows to `Input Data`, and new or changed products to `Master Data`.
2. Make sure every `PRODUCT ID` in `Input Data` exists in `Master Data`.
3. Refresh the report.
4. Check that the Total Sales card matches the total of the Excel sheet.

---

## Suggested improvements

- Show Profit and Profit % in every chart, and add a Discount % chart.
- Bind the treemap to Product, and add Top 10 and Bottom 10 product views.
- Add a Date table, and sort the month and day charts in date order.
- Create explicit measures (`Total Sales`, `Total Quantity`, `Profit %`).
- Fix the categories and units in Master Data.
- Add KPI comparisons (vs last month, vs last year, vs target).
- Add a mobile layout and a transaction drill-through page.

---

## Author and license

Yalabaka Abhinaya Sri ,
abhinayasri21@gmail.com 
