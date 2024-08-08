# Sales & Customer Analysis Dashboard


## Problem Statement

The organization is facing challenges in understanding and visualizing critical sales and customer data across multiple dimensions, including customer segmentation, geographical distribution, product categories, and time-based trends. The existing data was difficult to analyze cohesively, leading to inefficiencies in decision-making processes. The company required a comprehensive solution that could provide clear, actionable insights into customer behavior, sales performance, and profitability trends, with the ability to drill down into specific segments and time periods.

## **Tools**

- **Power BI:** For creating the interactive report dashboard.
- **DAX (Data Analysis Expressions):** To build dynamic calculations and advanced analytics.
- **Power Query:** For data cleaning and transformation.
- **Figma**: For designing the cover and layout of the dashboard.

## **Steps**

1. **Data Cleaning and Preparing:**
    - I gathered data related to customer demographics, sales figures, product categories, and geographic regions.
    - The data was then cleaned, ensuring consistency and accuracy, using Power Query.
2. **Data Modeling:**
    - Relationships between different datasets were established to create a comprehensive data model.
    - Calculated columns and measures were added using DAX to enable detailed analysis.
3. **Dashboard Design:**
    - The dashboard was divided into two main pages: **Customer Analysis** and **Sales Analysis**. This separation made it easier to focus on specific insights.
    - A user-friendly layout with a consistent color scheme and design was implemented to enhance the user experience.
4. **Visualization and Interactivity:**
    - I created various visualizations (bar charts, line charts, maps, and pie charts) to represent key metrics and trends.
    - Interactive elements like slicers, filters, bookmarks, and a page navigator were added to allow users to explore the data in depth.
5. **Analysis and Testing:**
    - DAX was used to calculate complex metrics like rolling sales, profit margins, and segment-wise contributions.
    - The dashboard was thoroughly tested to ensure all features and calculations worked as intended, and feedback was incorporated to refine the design.

## The Dashboard

![Sales Page.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/d774bcbe-f015-4aa5-b102-7b4ccde4ab34/4131783f-084e-4a7f-9727-345a8485ddee/Sales_Page.png)

![Customer Page.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/d774bcbe-f015-4aa5-b102-7b4ccde4ab34/5bab5114-efec-4b4b-9e33-8beca8fdc318/Customer_Page.png)

## **Key Findings**

- **Customer Segmentation:** The "Loyal" customer segment accounted for the largest portion of sales (44.54%), with top contributors like Horst Kloss driving significant revenue.
- **Geographical Insights:** The USA and Germany emerged as the top-performing markets, highlighting where the company should focus its efforts.
- **Product Performance:** Drinks and Cheese were the highest-grossing categories, but there’s potential for growth in categories like Fish and Deserts.
- **Sales Trends:** 2021 was a peak year in terms of sales and profitability, with slight declines in 2022, indicating the need for strategic adjustments.

## **Suggestions**

- **Retention Focus:** Strengthen customer retention efforts, particularly for the "Loyal" segment, through loyalty programs and personalized offers. And plan to
- **Market Expansion:** Expand marketing and product offerings in high-performing regions like the USA and Germany.
- **Marketing to Average Customers:** Develop targeted marketing campaigns aimed at converting "Average" customers into "Loyal" ones. This could include personalized discounts, exclusive deals, and enhanced customer engagement strategies.
- **Product Strategy:** Improve sales in lower-performing categories by exploring new marketing strategies or product enhancements.
- **Profit Margin Monitoring:** Keep a close eye on profit margins and explore cost optimization strategies to maintain profitability.
- **New Market Opportunities:** Consider expanding into underrepresented regions like Asia and South America for future growth.

# Snippet of Code

Here are some of the DAX formulas I developed for creating this dashboard and performing the analysis.

- DAX for Customer Classification

```DAX
ClassifiedCustomer = 
 CALCULATE([TotalSales],
 FILTER(
    VALUES('Order'[CustomerName]),
    COUNTROWS(
    FILTER(
        CustomerClassificationtbl,
        RANKX(ALL('Order'[CustomerName]),[TotalSales],,DESC)>= CustomerClassificationtbl[Min] && 
        RANKX(ALL('Order'[CustomerName]),[TotalSales],,DESC)<= CustomerClassificationtbl[Max])) > 0
        )
        )
```

- Profit percentage

```DAX
ProfitPercentage = DIVIDE([Profit],[TotalCost])
```

- Profit margin

```DAX
ProfitMargin = DIVIDE([Profit], [TotalSales])
```

Sales for last month corresponding to current month

```DAX
SalesLM = CALCULATE([TotalSales],DATEADD(Dates[Date],-1,MONTH))
```

Top sales by ranking category

```DAX
TopXSales = IF([Ranking]<=RankingParameter[RankingParameter Value],[TotalSales],BLANK())
```

Top sales by ranking category

```DAX
TopXSales = IF([Ranking]<=RankingParameter[RankingParameter Value],[TotalSales],BLANK())
```

## **Scope**

- **Real-Time Data Integration:** Incorporating real-time data could provide even more timely insights and allow for more dynamic decision-making.
- **Deeper Customer Insights:** Additional analysis on customer lifetime value and behavior patterns could further enhance strategic decisions.
- **Advanced Predictive Analytics:** Implementing predictive models could help forecast future trends and guide proactive strategies.

This dashboard is a robust tool for executives, providing a clear, interactive view of the company’s sales and customer landscape, and equipping them with the insights needed to drive growth and success.
