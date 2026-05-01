# Project 07: Product Performance Analysis
### Which Products Drive Revenue, Which Are Quietly Dying, and What the Sales Cycle Looks Like

---

## Business Brief

Most product catalogues follow an 80/20 pattern: a small number of products drive the majority of revenue while a large number sit generating minimal return. But which products fall into which category changes over time, and most businesses are too slow to notice.

This project analyses product-level sales performance and answers:

1. Which products and categories drive the most revenue?
2. How does performance change across months and quarters?
3. What does the order size distribution look like per product?
4. Which products are worth investing in vs phasing out?
5. How concentrated is the revenue base and what risk does that create?

---

## Dataset

| Property | Detail |
|----------|--------|
| **Name** | Sample Sales Data |
| **Direct Link** | https://www.kaggle.com/datasets/kyanyoga/sample-sales-data |
| **Records** | 2,800+ orders across multiple product lines |
| **Features** | Order date, product line, quantity, price, customer, territory |

---

## What Makes This Different

- Auto-detects file path and column names so it runs without manual path edits
- Uses SQL for all product-level aggregations
- Builds an 80/20 Pareto analysis with a cumulative curve
- Introduces the HHI Concentration Risk Score
- Classifies every product into a BCG-style performance quadrant
- Interactive treemap showing revenue hierarchy

---

## Project Structure

```
product-performance-analysis/
├── project_07_product_performance.ipynb
└── README.md
```

---

## Kaggle Setup

1. Search **"sample-sales-data"** by *kyanyoga* on Kaggle and attach it
2. Upload `project_07_product_performance.ipynb`
3. Run all cells - the notebook auto-detects the file path
4. If the path detection fails, check the output of Cell 2 and update `DATA_PATH` in Cell 3

---

## Notebook Walkthrough

### Section 1: Setup
Libraries, colour system. Amber = Star, Green = Cash Cow, Indigo = Question Mark, Red = Dog.

### Section 2: Load Data
Auto-detects all CSV files in the Kaggle input directory using glob. Tries multiple encodings automatically.

### Section 3: Prepare and Standardise
Standardises column names to lowercase. Auto-detects date, revenue, product, quantity, and order columns by searching for keywords. Parses dates, converts revenue to numeric, drops rows missing key values.

### Section 4: SQL Product Performance Queries
Three SQL queries:
- Revenue, order count, and average order value by product line
- Monthly revenue and order count trend
- Detailed product breakdown including units sold

### Section 5: Product Performance Charts
Four visualisations:
- Revenue and average order value horizontal bar charts
- Monthly revenue trend with order count (dual-axis area and bar)
- Revenue treemap coloured by average order value
- Quarterly revenue breakdown by product line

### Section 6: Pareto Analysis
Calculates cumulative revenue share across product lines. Dual-axis chart with revenue bars and cumulative percentage line. Prints exact number of products needed to reach 80% of revenue.

### Section 7: Quarterly and Seasonal Patterns
Grouped bar chart of revenue by quarter and product line. Prints best quarter by total revenue.

### Section 8: Concentration Risk Score
Calculates the Herfindahl-Hirschman Index (HHI) from revenue shares. Classifies the result (below 1,500 = diversified, 1,500-2,500 = moderate, above 2,500 = high risk). Revenue share donut chart and HHI gauge-style bar chart.

### Section 9: Product Performance Quadrant
BCG-style matrix classifying each product as Star, Cash Cow, Question Mark, or Dog based on revenue and order volume relative to median. Interactive scatter with threshold lines and product labels.

### Section 10: Executive Summary Dashboard
Dark-theme KPI cards: total revenue, total orders, top product line, best quarter, HHI score, star product count.

### Section 11: Findings and Recommendations
Five findings with evidence. Four recommendations with specific actions.

---

## Key Findings

| Finding | Evidence |
|---------|----------|
| A small number of product lines dominate total revenue | Pareto analysis |
| Revenue concentration is measurable with the HHI score | Concentration analysis |
| Product lines differ significantly in average order value | AOV chart |
| Clear seasonal patterns exist across quarters | Quarterly analysis |
| Each product line has a distinct strategic profile | BCG quadrant matrix |

---

## Tools Used

| Tool | Purpose |
|------|---------|
| Python (Pandas, NumPy) | Data manipulation, column auto-detection |
| SQLite3 | Product aggregation queries |
| Plotly | Treemap, scatter quadrant, trend lines |
| Matplotlib | Pareto chart, concentration risk gauge |
| Seaborn | Supporting visualisations |

---

*Built by Jessica Dan-Odhomo - [LinkedIn](https://www.linkedin.com/in/jessica-dan-odhomo) - [GitHub](https://github.com/Teekaayyy)*
