# E-Commerce-Analysis-001-

<p align="center">
  <img src="images\dashboard.png" alt="Dashboard" width="100%">
</p>

<div align='center'>
The <a href="https://www.kaggle.com/datasets/prince7489/e-commerce-sales">E commerce Sales Dataset</a> is a synthetic dataset but a realistic sample of the e commerce sales data of online shops. I am going to analyze the data and transform it into an analytical dashboard to see what are some lucrative key performance findings that are essential to improving company performance.  
</div>
<br>

<div> 
But first we have to get essential questions. Questions that are asked by stakeholders. Questions that are essential on driving-data driven decisions and evaluate overall efficacy. 
<br>
Request 1: Executive Pulse Check (Is the business healthy?)
<br>
Request 2: The "Discount Trap" Investigation (Are discounts killing us?)
<br>
Request 3: Regional & Urban Performance (Where should we expand?)
<br>
Request 4: Payment Preferences (Transaction Efficiency) What payment method do our customers use the most? Is digital payment (UPI) growing?
<br>
</div>

<div align='center'>
Before diving into the dashboard we have to see the data itself. If there are null values. And what are essential columns that I can add (Unit Cost, quarter season, etc.) and If there are errors to it. there are many ways to manipulate the data like using sql. But now I am going to use python to look into the dataset.
 </div>
<br>
<div>
Looking at the data:
</div>

```python
print('Missing values Percentage: \n\n', round(df.isnull().sum().sort_values(ascending=False)/len(df)*100,1))

```
<div align='center'>
We see that the data does not have missing or null values. 
 </div>

<p align="center">
  <img src="images\missing-values-percentage.png" alt="Missing Values percentage" width="100%">
</p>
<br>
<div align='center'>
We see that there is the unit price Unit Price (what the customer paid) and Profit (what the company kept), but it doesn't explicitly state how much it actually cost the company to manufacture or acquire the product. So there is a need to add the cost of the unit.
 </div>

```python
df['Unit Cost'] = round(df['Unit Price'] - (df['Profit'] / df['Quantity']),2)

```
<br>
<div align='center'>
now we that the first request is: <br> Request 1: Executive Pulse Check (Is the business healthy?)
to see that the business is healthy we have to look at the sum of profit annually and quarterly. 
</div>
<br
<p align="center">
  <img src="images\sum of profits by year and quarter.png" alt="sum of profit margin by Year and quarter" width="100%">
</p>
<br>
<div align='center'> 
We see that profits are stable but are not growing. In the final quarter. There is only small set of data that didn’t fully cover the full 4th quarter. It 10 rows of data in October. No more in November, and December. <br>
Looking at the profit margin we see that profits are stable. Which were around 15 percent but then dipped as of the final quarter of 2025 it dipped. 
</div>
<p align="center">
  <img src="images\profitMargin-by-YearandQuarter.png" alt="profit margin" width="100%">
</p>
<div align='center'>
 Looking at the average over value. To look into customer transaction, we see that there is stability. But there is a dip in the final year. 
<div>
<p align="center">
  <img src="images\AOV.png" alt="AOV" width="100%">
</p>
<div align='center'>Looking at the average order value. We see that last year was in a better position in overall average. If u compare the final quarter of 2025 and 2024, there is a striking difference. <br>
Request 2: The "Discount Trap" Investigation (Are discounts killing us?)
 </div>
 <p align="center">
  <img src="images\discount.png" alt="dscount" width="100%">
</p>
<div align='center'>
Let’s look at the profit margin and profit with discounts. Looking at the profit margin there isn’t much of striking difference between discount with 0 and 20 percent. Which is quite questionable. And looking at the sum of profit we see that as the discounts increased. The profit decreases. (I find the data questionable here as in the real word. Bad discounting can cause a massive negative losses. But in this dataset, negative profit does not exist). <br>
Request 3: Regional & Urban Performance (Where should we expand?)

 </div>

<p align="center">
  <img src="images\profit_by_city.png" alt="cities" width="100%">
</p>
<div align='center'>
Looking at the top cities we see that there isn’t a massive descent between them but a slow gradual decrease of profit.  Strongest top 3 links are from Lucknow, Guwahati, Bangalore. The least cities are from Coimbatore, Hyderabad and Thiruvana. In the middle are the Delhi Goa and pune. 
<br>
Request 4: Payment Preferences (Transaction Efficiency)
</div>
<p align="center">
  <img src="images\payment mode chart.png" alt="pie chart payment mode" width="100%">
</p>
<div align='center'>
Looking at the payment mode. They are almost all identical. Comparing to real world scenario. This can be further from the truth. UPI and COD usually dominates the mode of payment. My theory is that the making of this dataset is they used Uniform Random Distribution.  
</div>