# 📊 Power BI Assignment 2 – DAX & Data Visualization

## 📌 Project Overview

This project focuses on analyzing an E-commerce Sales Dataset using Microsoft Power BI, DAX (Data Analysis Expressions), and interactive data visualizations.

Building on the previous data transformation and data modeling assignment, this project involves creating calculated columns, measures, and business metrics using DAX. It also includes developing interactive visualizations to analyze sales performance, profitability, sales targets, order distribution, and regional sales trends.

The objective is to transform raw business data into meaningful insights that support data-driven decision-making.

## 🎯 Project Objectives

- Create calculated columns using DAX.
- Develop measures to calculate key business metrics.
- Analyze sales performance and profitability.
- Calculate order counts, average profit, and Year-to-Date sales.
- Compare actual sales against sales targets.
- Build interactive charts and visualizations.
- Analyze sales trends across months, categories, and sub-categories.
- Explore geographic sales distribution.
- Present business insights through an interactive Power BI report.

## 📂 Dataset Description

This project uses three related datasets from an E-commerce Sales Dataset.

### 1. List of Orders

| Column | Description |
|---|---|
| Order ID | Unique order identifier |
| Order Date | Date of the order |
| Customer Name | Customer's name |
| City | Customer's city |
| State | Customer's state |
| Category | Product category |
| Amount | Order amount |
| Profit | Profit or loss generated |

### 2. Order Details

| Column | Description |
|---|---|
| Order ID | Identifier used to connect order records |
| Category | Product category |
| Sub-Category | Product sub-category |
| Quantity | Quantity sold |
| Amount | Amount associated with the order details |
| Profit | Profit associated with the order details |

### 3. Sales Target

| Column | Description |
|---|---|
| Category | Product category |
| Month of Order Date | Month associated with the sales target |
| Target | Sales target amount |

## 🛠️ Tools and Technologies

- **Microsoft Power BI** – Data analysis and visualization
- **DAX** – Calculated columns and analytical measures
- **Data Modeling** – Relationships between tables
- **Power Query Editor** – Data preparation and transformation
- **Interactive Visualizations** – Business reporting and analysis

# 🧮 DAX Calculations

## 1. Calculated Columns

### 🔹 Category Type

Created a calculated column in the Order Details table by combining Category and Sub-Category.

```dax
Category Type =
'Order Details'[Category] & " - " &
'Order Details'[Sub-Category]
```

**Purpose:** To provide a combined category label for detailed product analysis.

### 🔹 Revenue per Order

Created a calculated column to calculate revenue using Amount multiplied by Quantity.

```dax
Revenue per Order =
'Order Details'[Amount] *
'Order Details'[Quantity]
```

**Purpose:** To calculate revenue based on the amount and quantity fields, as specified in the assignment.

*Note: Confirm the meaning of the Amount column before interpreting this metric as actual revenue, since Amount may already represent the total line-item value.*

### 🔹 Sales Category

Created a calculated column to classify sales as Above Average or Below Average based on Amount.

```dax
Sales Category =
IF(
    'Order Details'[Amount] >
        AVERAGE('Order Details'[Amount]),
    "Above Average",
    "Below Average"
)
```

**Purpose:** To categorize sales records according to the average Amount across the Order Details table. Records equal to the average are classified as Below Average in this formula.

## 2. Calculated Measures

### 🔹 Order Count

Created a measure to count orders in the Order Details table.

```dax
Order Count =
DISTINCTCOUNT('Order Details'[Order ID])
```

**Purpose:** To calculate the number of unique orders. Use `COUNTROWS` instead if the requirement is to count every row or order-detail record.

### 🔹 Average Profit in Delhi

Created a measure to calculate the average profit for orders placed in Delhi.

```dax
Average Profit in Delhi =
CALCULATE(
    AVERAGE('List of Orders'[Profit]),
    'List of Orders'[City] = "Delhi"
)
```

**Purpose:** To evaluate average profitability for orders associated with Delhi.

### 🔹 Year-to-Date (YTD) Sales

Created a measure to calculate cumulative sales from the beginning of the year through the current date in the selected filter context.

```dax
YTD Sales =
TOTALYTD(
    SUM('List of Orders'[Amount]),
    'List of Orders'[Order Date]
)
```

**Purpose:** To track cumulative sales performance throughout the year.

*Note: For reliable time-intelligence calculations, use a proper Date table with a relationship to Order Date. The measure also respects the report's filter context.*

# 📈 Data Visualization

The following visualizations are included in the assignment.

### 1. Sales Target Achievement by Category

**Visual:** Clustered Column Chart

- Compare actual sales with sales targets.
- Identify categories performing above or below target.
- Evaluate category-level sales performance.

### 2. Maximum Profit Margin by Sub-Category

**Visual:** Donut Chart

- Display maximum profit margin across sub-categories.
- Compare the highest profit margin values.
- Identify sub-categories with relatively high margins.

### 3. Monthly Sales Trend

**Visual:** Line Chart

- Analyze sales performance over time.
- Identify monthly fluctuations and trends.
- Understand changes in sales performance.

### 4. Profit and Quantity by Sub-Category

**Visual:** Scatter Chart

- Compare profit against quantity sold.
- Identify sub-categories with high sales volume and profitability.
- Explore relationships between quantity and profit.

### 5. Total Sales Amount and Target

**Visuals:** Card and Multi-row Card

- Display total sales amount.
- Display total sales target.
- Show minimum target values across relevant segments.
- Support quick comparison of actual performance and targets.

### 6. Sales Performance Matrix

**Visual:** Matrix

- Compare actual sales and targets by category and month.
- Identify sales performance patterns.
- Examine performance across different reporting periods.

### 7. Geographic Sales Analysis

**Visual:** Map

- Visualize sales by city.
- Identify regional sales patterns.
- Compare sales performance across geographic locations.

### 8. Sales Distribution by Sub-Category

**Visual:** Treemap

- Represent sales distribution across sub-categories.
- Identify sub-categories contributing larger sales amounts.
- Compare the relative contribution of different product groups.

### 9. Order Count Analysis by State

**Visual:** Funnel Chart

- Visualize order counts across states.
- Compare the volume of orders across geographic regions.
- Identify states with relatively high and low order counts.

# 💡 Key Business Questions

This project supports the investigation of questions such as:

- Which product categories are meeting their sales targets?
- How do sales trends change from month to month?
- Which sub-categories generate higher profits?
- How does quantity sold relate to profitability?
- What is the average profit for orders placed in Delhi?
- How are sales distributed across cities and states?
- Which categories and sub-categories contribute most to sales?
- How does cumulative YTD sales performance change over time?

## 📊 Expected Outcomes

- Improved understanding of DAX calculated columns and measures.
- Clear comparisons between actual sales and targets.
- Better visibility into sales and profit trends.
- More effective analysis of category and sub-category performance.
- Interactive visualizations for geographic and time-based analysis.
- A foundation for communicating business insights through Power BI reports.

## 🧠 Skills Demonstrated

- DAX Calculated Columns
- DAX Measures
- `IF`
- `CALCULATE`
- `AVERAGE`
- `DISTINCTCOUNT`
- `TOTALYTD`
- Sales and Profitability Analysis
- KPI Reporting
- Data Visualization
- Time-Series Analysis
- Geographic Analysis
- Business Intelligence Reporting

## 📁 Project Files

- `DashBoard 2..pbix` – Power BI project file containing the report and DAX calculations.

## 🎓 Learning Outcomes

Through this project, I strengthened my understanding of DAX calculations, analytical measures, and interactive data visualization in Power BI.

I learned how to create business metrics, compare sales against targets, analyze profitability, track sales trends, and present data through different visualization techniques.

This project represents the next stage of my learning journey, moving from data cleaning and data modeling toward business analysis and dashboard development.

## 👩‍💻 About Me

I am an **Aspiring Data Analyst** developing my analytical and technical skills through hands-on projects.

My learning journey includes:

**Microsoft Excel | SQL | Python | Power BI | DAX | Data Analytics**

I am continuously building practical projects to strengthen my skills and develop a professional Data Analyst portfolio.
