# Retail Profit Analysis – End-to-End Project
## Retail Dashboard

**Download Power BI File (.pbix)**  
🔗(https://drive.google.com/drive/folders/1VLjdfnNDbSCjrVy7FPoBNUWoGRdVPNIn)

Understanding where profit is strong, where it is weak, and why margin erosion is happening. 
## Problem Statement

This project investigates the profitability patterns of a large retail business to answer one of the most important questions in retail:

  #### Where are we losing profit margin, and what is causing it?

While high sales can look impressive, the real health of the business depends on profit, margin stability, and cost efficiency.
This project identifies whether certain regions, product categories, or cost factors, like discounts or shipping expenses, are quietly reducing profit.

The final goal is to provide clear, data-backed insights and recommendations that the business can act on.

## Business Context

Retail companies often focus on revenue growth, but revenue alone doesn’t guarantee success.

A business may:

Sell high volumes
Give frequent discounts
Spend more on shipping
Stock low-margin products and still struggle with real profitability.

Profit margin tells the deeper story:

Which categories are hurting the business
Which regions are inefficient
Where discounts are too aggressive
Which products drive growth vs. erosion

This project analyses profit margins across 1M+ retail transactions to help decision-makers optimize:

Pricing
Discount policies
Shipping strategy
Product selection
Regional investment

## Dataset Overview

Source: Data.World (Retail Transactions Dataset)
Size: 1,000,000+ rows
Columns: 20+ fields

#### Key columns used:
customer_segment
product_category
profit, profit_margin, sales
discount
shipping_cost
region
order_date, order_quantity
customer_name, customer_age, city

The dataset is large enough to show real patterns often seen in actual retail environments.

## Data Cleaning & Preparation
- Removed corrupted & blank rows
  Checked missing values for:
  customer_segment  
  order_priority  
  profit  
  profit_margin  
  sales  
  shipping_cost  

  Removed rows with missing critical numeric fields.

- Cleaned messy city fields

  Used Excel helper formula:

  =IF(ISNUMBER(FIND(",", A2)),"Remove", "Keep")

  This flagged city names with commas or multiple values.
  Around 20,000 rows were dropped — only 2% of the dataset — improving data consistency.

- Standardized category & text fields
  Trimmed whitespace
  Replaced missing segments with “Not Specified”
  Ensured numerical columns were properly typed

The dataset was validated again before analysis.

 ## EDA was performed in Python using Pandas, NumPy, Seaborn, and Matplotlib.

### Average Profit Margin

Overall average profit margin ≈ 37%

➡ The business is healthy on average, but averages hide hidden issues.
So, deeper category & region analysis was needed.

![Chart](https://github.com/sangralArsha/Retail-Profit-Analysis/blob/main/Expolatory%20Data%20Analysis.png)


### Profit Margin by Product Category

Furniture: 45.3%
Technology: 41.5%
Office Supplies: 31.7% (lowest)

➡ Office Supplies consistently shows weak profitability and many low-profit outliers.

![Chart](https://github.com/sangralArsha/Retail-Profit-Analysis/blob/main/EDA%202%20.png)

### Profit Margin by Region

Margins across East, West, Central, and South were close in EDA (~36–37%).
This suggested region alone wasn’t the main problem — but combining region + category might reveal more.

### Profit Margin by Customer Segment

Corporate, Consumer, Home Office, and Small Business all sat between 36–38%.

➡ Customer segment isn’t a major source of margin erosion.

### Discount vs Profit Margin

One of the clearest patterns:

As the discount increases, the margin drops sharply.

Office Supplies is hit the hardest by discounts.

![Chart](https://github.com/sangralArsha/Retail-Profit-Analysis/blob/main/EDA%203.png)

➡ High discounting is a major driver of weak profitability.

## Power BI Dashboards

I created two dashboards:

### Dashboard 1: Retail Profit Dashboard (Overview)

![Chart](https://github.com/sangralArsha/Retail-Profit-Analysis/blob/main/overall%20dashboard.png)

INSIGHTS

1. Revenue is strong but margin is slightly declining.
While sales remain high, margin erosion suggests rising costs or over-discounting.

2. Monthly profit margins are stable but not improving.
Margins trend around ~37% with minimal month-to-month movement.

3. South region is the weakest.
Compared to East, West, and Central, South consistently returns lower profit margin.

4. Office Supplies category underperforms.
Lowest profit margin, lowest revenue, and slow movement, consistently poor results across panels.

5. Technology is the strongest category.
High sales + strong margins make Technology the profit engine of the business.

6. Margin erosion is significant.
KPI shows notable erosion despite revenue growth.

### Dashboard 2: Retail Profit Analysis (Deep Dive)

(Identifying exact causes of margin loss)
![chart](https://github.com/sangralArsha/Retail-Profit-Analysis/blob/main/Profit%20analysis.png)

INSIGHTS

1. South region produces the least profit.
When narrowed by year/quarter, South consistently shows the lowest profit.

2. Office Supplies is the weakest category.
Every low-profit or loss-making product comes from Office Supplies.

3.OIC Thumb Tacks is the weakest product from office supplies

4. High discounts strongly reduce profit margins.
Scatterplot confirms: Discounts > 10–20% destroy margins.

5. Shipping cost further reduces margin.
Higher shipping = lower margin, especially in South and in Office Supplies.

6. Decomposition tree confirms the root cause.
Path:
South → Office Supplies → High Discount Group → High Shipping Cost

This is the biggest driver of overall margin erosion.

6. Least profitable products cluster in the same category.
All top 5 worst products fall under Office Supplies.

##  Combined Recommendations (for both dashboards)
### Reduce discounts on low-margin categories

Office Supplies should have strict discount caps (e.g., 10%).


### Reconsider pricing strategy for Office Supplies

Increase prices where possible

Reevaluate supplier costs

Remove consistently unprofitable SKUs

### Improve logistics, especially in South

Route optimization

Carrier negotiation

Local micro-fulfilment centers

Shipping cost is a major margin killer.

### Promote high-margin categories more

Technology products should be prioritized for:

Homepage placements

Ads & promotions

Bundles & upsells

### Implement margin guardrails

Before approving a discount or promotion:

Check expected post-discount margin.

Set automated alerts for margin dropping below a threshold.

###  Track margin erosion consistently

Set up monthly reviews using the Profit Analysis dashboard.

## Tools Used

Python (Pandas, NumPy, Seaborn, Matplotlib)

Power BI (interactive dashboarding, DAX measures, modelling)

Excel (quick cleaning and quality checks)

## Final Summary

This project highlights how a business can appear strong on the surface (good revenues, good average margins) while still suffering from deeper structural issues in:

Discount strategy

Category profitability

Regional cost efficiency

Shipping overhead

By combining Python EDA with Power BI storytelling, I was able to uncover exactly where profit is leaking and provide actionable, business-friendly recommendations.
