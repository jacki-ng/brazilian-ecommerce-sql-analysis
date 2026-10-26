# Behind the Checkout: Brazilian E-Commerce with SQL

**A personal SQL project exploring sales, payment habits and the customer experience.**

I started this project while preparing my application for a trainee position at the FINMA. I'm genuinely motivated by the opportunity to work at FINMA, and I wanted to take the initiative to learn the basics of SQL.

I chose Brazilian e-commerce data and started with a fairly simple question: what was behind the rapid growth of an online marketplace? As I explored the data, I became just as interested in what happens around a purchase—how customers pay, which products generate sales, and whether deliveries arrive when promised.

Using the [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce), I connected order, payment, product, customer and review data in SQLite. The dataset contains nearly 100,000 orders from 2016–2018. I used Python to load the data and create the charts, but the business analysis itself is written in SQL.

**[Explore the full analysis in my Jupyter Notebook](Olist_SQL_Business_Analysis.ipynb)**

## What I wanted to find out

- Was sales growth driven by more orders or higher spending per order?
- Which payment methods accounted for the most transaction value?
- Which product categories contributed most to sales?
- Where were deliveries most frequently delayed?
- How did delivery delays relate to customer reviews?

## Key findings

**1. Sales growth came mainly from order volume.**  
For January–August 2018 versus the same period in 2017, item sales from delivered orders increased by **141.1%** (BRL 7.22 million versus BRL 2.99 million). The number of delivered orders rose by **139.9%**, while average item-sales value per order was almost unchanged (+0.5%). Growth was largely a matter of processing more orders, rather than customers spending more on each one.

**2. Credit cards dominated the payment mix.**  
Credit cards represented **78.5%** of recorded payment value, followed by *boleto*—a commonly used Brazilian payment slip—at **18.0%**. Vouchers and debit cards accounted for much smaller shares.

**3. Delivery reliability varied by region.**  
Among states with at least 500 delivered orders, Maranhão had the highest late-delivery rate (**17.5%**). Rio de Janeiro had a lower rate (**12.1%**) but far more affected orders (**1,495**). Both the percentage and the number of customers affected matter when assessing operational issues.

**4. Late deliveries went hand in hand with poorer reviews.**  
Orders delivered late had an average review score of **2.27/5**, compared with **4.29/5** for orders delivered on time or early. This is a strong descriptive association, although it doesn't establish that delays caused the lower ratings.

## How I approached the analysis

I worked with seven related tables and used SQL joins, grouping, aggregations, `CASE WHEN`, `COUNT(DISTINCT)`, common table expressions (CTEs), views and date comparisons.

One important step was getting the level of detail right. An order can contain several items and multiple payment records, so joining those tables without care can inflate totals. I aggregated item prices to the order level and reconciled the result against a separate calculation from the original item records.

## Explore or reproduce the notebook

The notebook includes the **SQL queries, executed results, five charts and my interpretation of the findings**. GitHub displays its saved outputs without requiring Jupyter to be installed.

To run the analysis:

1. Download the original dataset from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).
2. Place the downloaded ZIP beside the notebook and name it `archive.zip`.
3. Open `Olist_SQL_Business_Analysis.ipynb` in JupyterLab or Jupyter Notebook. You'll need Python with `pandas` and `matplotlib` installed.
4. Restart the kernel and run all cells.

The source CSVs are not included in this repository.


**Data source:** Olist, *Brazilian E-Commerce Public Dataset*, [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).
