# Task 1: Connect and Inspect Data

## Objective

The objective of this task was to connect the retail sales dataset (`dashboard_sales_data.xlsx`) to Tableau and verify that all fields were assigned the correct data types and roles before creating visualizations and dashboards.

---

## Dataset Loaded

- **File Name:** dashboard_sales_data.xlsx
- **Tool Used:** Tableau Desktop
- **Data Source:** Microsoft Excel

The dataset was successfully connected using the Tableau Excel connector.

---

## Data Type Inspection

After loading the dataset, all fields were reviewed to ensure they were correctly identified by Tableau.

### Date Fields

The following fields were verified as **Date** data types:

- Order Date
- Ship Date

These fields will be used for time-based analysis, trend charts, and monthly/yearly reporting.

---

### Geographic Fields

The following fields were assigned the appropriate Geographic Roles:

- Region
- State
- City

These fields enable geographic analysis and support regional performance reporting.

---

### Categorical Fields (Dimensions)

The following fields were treated as Dimensions because they contain descriptive information:

- Order ID
- Customer Name
- Customer Segment
- Category
- Sub-Category
- Ship Mode
- Payment Status
- Order Status
- Campaign Channel

These fields are used for grouping, filtering, and comparison in the dashboard.

---

### Numerical Measures

The following fields were verified as Measures:

- Sales
- Profit
- Quantity
- Discount
- Delivery Days
- Customer Rating

These fields are used in calculations, KPIs, and visualizations.

---

### Binary / Flag Fields

The following field was identified as a binary (Yes/No) field:

- Return Flag

This field is used for return analysis and calculating the Return Rate.

---

## Assumptions

The following assumptions were made during data inspection:

- Order Date and Ship Date contain valid date values and are suitable for time-series analysis.
- Region, State, and City represent valid geographic information and were assigned appropriate geographic roles.
- Sales, Profit, Quantity, Discount, and Delivery Days contain numeric values and were treated as measures.
- Return Flag contains only valid Yes/No values.
- Customer-related and product-related fields are categorical dimensions used for filtering and segmentation.
- Any missing or inconsistent values should be addressed before creating dashboard visualizations.

---

## Outcome

The dataset was successfully connected and inspected. All fields were assigned appropriate data types and roles, ensuring the data is ready for creating calculated fields, charts, dashboards, and business insights in the subsequent tasks.



# Task 2: Create Calculated Fields

## Objective

The objective of this task was to create calculated fields in Tableau that provide meaningful business metrics for analyzing sales performance, profitability, customer behavior, shipping efficiency, and return patterns. These calculated fields were used throughout the dashboard to support executive decision-making.

---

## Calculated Fields Created

### 1. Profit Margin

**Formula**

```tableau
SUM([Profit]) / SUM([Sales])
```

**Purpose**

Calculates the percentage of profit earned from total sales.

**Business Value**

Helps identify how efficiently the business converts sales into profit and compares profitability across regions, categories, and customer segments.

---

### 2. Cost

**Formula**

```tableau
SUM([Sales]) - SUM([Profit])
```

**Purpose**

Calculates the estimated cost incurred to generate sales.

**Business Value**

Allows management to compare costs with revenue and identify areas where operational expenses may be high.

---

### 3. Average Order Value (AOV)

**Formula**

```tableau
SUM([Sales]) / COUNTD([Order ID])
```

**Purpose**

Calculates the average sales value per customer order.

**Business Value**

Measures customer purchasing behavior and helps evaluate pricing strategies and promotional campaigns.

---

### 4. Return Rate

**Formula**

```tableau
SUM([Return Flag])
/ COUNT([Order ID])
```

**Purpose**

Calculates the percentage of returned orders compared to the total number of orders.

**Business Value**

Identifies products, regions, or customer segments with high return rates, helping improve product quality and customer satisfaction.

---

### 5. Shipping Delay Bucket

**Formula**

```tableau
IF [Delivery Days] <= 2 THEN
    "Fast"

ELSEIF [Delivery Days] <= 5 THEN
    "Normal"

ELSE
    "Delayed"

END
```

**Purpose**

Groups delivery times into three categories based on shipping duration.

**Business Value**

Provides an easy way to evaluate shipping performance and identify delays that may affect customer experience.

---

## Summary of Calculated Fields

| Calculated Field | Business Purpose |
|------------------|------------------|
| Profit Margin | Measures profitability as a percentage of sales |
| Cost | Calculates estimated business cost |
| Average Order Value | Measures average revenue generated per order |
| Return Rate | Calculates the proportion of returned orders |
| Shipping Delay Bucket | Categorizes deliveries into Fast, Normal, and Delayed |

---

## Assumptions

- Sales and Profit contain valid numeric values.
- Order ID is unique and represents a single customer order.
- Return Flag contains only valid values such as **Yes** and **No**.
- Delivery Days is calculated correctly from the difference between Ship Date and Order Date.
- Division by zero is not expected because sales and order counts are assumed to be greater than zero.

---

## Outcome

The calculated fields provide meaningful business metrics that support dashboard visualizations, KPI cards, profitability analysis, shipping performance monitoring, and return analysis. These calculations improve the quality of business insights and enable leadership to make data-driven decisions.

# Part 4: Tableau Executive Dashboard

## Business Problem Summary

The retail company's leadership team requires an interactive executive dashboard to monitor key business performance indicators, including sales, profitability, customer segments, regional performance, shipping efficiency, discount impact, and return patterns. The objective is to provide a centralized, data-driven dashboard that enables leadership to identify trends, business risks, and growth opportunities, ultimately supporting strategic decision-making.

---

# Dataset Description

**Dataset Name:** `dashboard_sales_data.xlsx`

The dataset contains retail transaction records with information such as:

- Order ID
- Order Date
- Ship Date
- Customer Name
- Customer Segment
- Region
- State
- City
- Category
- Sub-Category
- Sales
- Profit
- Discount
- Quantity
- Ship Mode
- Delivery Days
- Return Flag
- Payment Status
- Order Status

The dataset was imported into Tableau Desktop for visualization and business analysis.

---

# Tableau Workbook Description

**Workbook Name:** `executive_dashboard.twbx`

The Tableau workbook contains:

- Data source connection
- Calculated fields
- Individual worksheets
- Interactive executive dashboard
- Dashboard filters
- Dashboard actions
- KPI cards

The dashboard was designed for leadership to quickly evaluate business performance and identify opportunities for improvement.

---

# Calculated Fields Created

The following calculated fields were created in Tableau:

| Calculated Field | Purpose |
|------------------|---------|
| Profit Margin | Calculates profitability as Profit ÷ Sales |
| Cost | Calculates Cost = Sales − Profit |
| Average Order Value | Calculates average revenue per order |
| Return Rate | Calculates returned orders as a percentage of total orders |
| Shipping Delay Bucket | Classifies delivery into Fast, Normal, or Delayed categories |

### Shipping Delay Bucket Formula

```tableau
IF [Delivery Days] <= 2 THEN
    "Fast"
ELSEIF [Delivery Days] <= 5 THEN
    "Normal"
ELSE
    "Delayed"
END
```

---

# Dashboard Components

The Executive Dashboard includes the following visualizations:

- Sales Trend (Line Chart)
- Regional Performance (Horizontal Bar Chart)
- Category Profitability (Horizontal Bar Chart)
- Customer Segment Performance (Stacked Bar Chart)
- Shipping Performance (Bar Chart)
- Discount vs Profit (Box-and-Whisker Plot)
- Return Analysis (Bar Chart)

### KPI Cards

- Total Sales
- Total Profit
- Profit Margin
- Total Orders
- Return Rate

---

# Filters and Interactions Used

The dashboard includes interactive filters that allow users to analyze data dynamically.

### Filters

- Region
- Category
- Customer Segment
- Ship Mode
- Order Date

### Dashboard Interactions

- Cross-filtering between charts
- Interactive dashboard filtering
- Dynamic highlighting
- Drill-down capability where applicable

These interactions enable leadership to explore business performance from multiple perspectives.

---

# Key Business Insights

The dashboard provides several important business insights, including:

- Sales trends over time reveal seasonal patterns.
- High-performing regions contribute significantly to revenue and profit.
- Certain product categories generate higher profit margins than others.
- Customer segments differ in purchasing behavior and profitability.
- Higher discount levels often reduce profit margins.
- Shipping performance varies across shipping modes.
- Product returns are concentrated in specific categories or regions.
- Opportunities exist to improve profitability through optimized pricing and operational efficiency.

---

# Dashboard Story Summary

The dashboard presents a complete business performance overview by connecting sales trends, regional performance, product profitability, customer behavior, shipping efficiency, discount strategies, and return patterns.

Rather than presenting individual charts independently, the dashboard tells a unified business story that helps leadership understand current performance, identify operational risks, and discover opportunities for business growth. The interactive design enables users to filter data, compare performance across dimensions, and make informed decisions based on real-time business metrics.

---

# Assumptions and Limitations

## Assumptions

- All sales and profit values are accurate.
- Order Date and Ship Date contain valid dates.
- Delivery Days correctly represent shipping duration.
- Return Flag contains valid Yes/No values.
- Profit Margin and Return Rate calculations are based on available data.
- Geographic fields are correctly assigned for regional analysis.

## Limitations

- The dashboard is based only on the provided historical dataset.
- External business factors such as economic conditions, competitor activity, and customer satisfaction are not included.
- Forecasting and predictive analytics are outside the scope of this dashboard.
- Missing or inaccurate source data may affect dashboard results.

---

# Screenshots Included

The repository includes the following screenshots as evidence of completed work:

| Screenshot | Description |
|------------|-------------|
| `full_dashboard.png` | Complete Executive Dashboard |
| `sales_trend_view.png` | Sales Trend Line Chart |
| `regional_performance_view.png` | Regional Performance Analysis |
| `category_profitability_view.png` | Category and Sub-Category Profitability |
| `filter_interaction_view.png` | Dashboard Filter Interaction |

All screenshots are stored in the **screenshots/** folder and demonstrate the completed Tableau dashboard and interactive features.

---

# Repository Structure

```
part4_tableau_dashboard/
│
├── data/
│   └── dashboard_sales_data.xlsx
│
├── tableau/
│   └── executive_dashboard.twbx
│
├── outputs/
│   ├── dashboard_story.md
│   ├── business_insights.md
│   └── chart_selection_justification.md
│
├── screenshots/
│   ├── full_dashboard.png
│   ├── sales_trend_view.png
│   ├── regional_performance_view.png
│   ├── category_profitability_view.png
│   └── filter_interaction_view.png
│
└── README.md
```

---

# Tools Used

- Tableau Desktop
- Microsoft Excel
- GitHub
- Markdown

---

# Conclusion

The Executive Tableau Dashboard successfully transforms retail sales data into an interactive business intelligence solution. By combining KPIs, trend analysis, profitability metrics, customer segmentation, shipping performance, and return analysis, the dashboard provides leadership with actionable insights for improving operational efficiency, increasing profitability, and supporting strategic business decisions.