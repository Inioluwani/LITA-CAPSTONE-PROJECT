# LITA-CAPSTONE-PROJECT
This where I document my capstone project for my LITA Data Analysis class with the incubator hub. Here, I analysed the sales data provided.

[Project Title](#project-title)

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Data Cleaning and Preparation](#data-cleaning-and-preparation)

[Exploratoratory Data Analysis](#exploratoratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

[Observation from Visualizations](#observation-from-visualizations)

[Recommendation from Analysis](#recommendation-from-analysis)


### Project Title: Sales Data Analysis

### Project Overview
This data analysis project was done on a sales data where a number of clothing items were sold in different regions of the country. The analysis is to tell stories on the sales and revenue track for the clothing items. This also to make decisions based on facts on how clothing items are to be sold.

### Data Sources
Data was provided by the Incubator hub to be used for the project. The Primary data used here is sales data.xlsx

### Tools Used
- Microsoft Excel : This was used for:
  1.  data cleaning
  2.  analysis 
  3.  creation of pivot tables
- Structured Query Language - This was used to query the data to provide data answers and trends.
  
- Power BI - This was used to create various data visualizations.
  
- GitHub- This was used to document the project.
  
### Data Cleaning and Preparation
Data was cleaned using microsoft excel. Duplicate rows were deleted by using the data ribbon. Data was filtered by column to detect blank spaces. The column names were formatted properly.

### Exploratoratory Data Analysis
EDA involved answering some questions about the sales data such as;
- what is the average sales per product?
- Whatis the total revenue by region?
- What is the total revenue by product?
- Who are the top 5 customers by purchases?
- What are the top performing products?

 ### Data Analysis
 This is where I include excel formulas, basic lines of queries from SQL and some 
 DAX expressions from PowerBi used during my analysis;
 
 SQL

``` SQL
Create database LITA_Project_1
Select * from [dbo].[LITA Capstone Sales Data Dataset]

-----total sales per product

select sum(Quantity) as total_sales,[Product] from [dbo].[LITA Capstone Sales Data Dataset]
group by [Product]

------total revenue per product

select sum([UnitPrice] *[Quantity] ) as total_revenue,[Product] from [dbo].[LITA Capstone Sales Data Dataset]
group by [Product]

-----number of transactions by region

select COUNT([Customer_Id]) as transactions ,[Region] from [dbo].[LITA Capstone Sales Data Dataset]
group by [Region]

-----highest selling product

select top 1 sum(Quantity) as total_sales,[Product] from [dbo].[LITA Capstone Sales Data Dataset]
group by [Product]
order by 1 desc

------top 5 customers by total purchase amount 

select top 5 sum([Quantity]*[UnitPrice] ) as purchase_amount, [Customer_Id] from [dbo].[LITA Capstone Sales Data Dataset]
group by [Customer_Id]
order by 1 desc 

------monthly sales total

select sum(Quantity) as monthly_sales,[OrderDate] from [dbo].[LITA Capstone Sales Data Dataset]
group by [OrderDate]
having [OrderDate] >= '2024-01-01'
order by 2 asc

-----products not sold in the last quarter

select [Product] from [dbo].[LITA_Capstone_Dataset]
where [Product] not in(
select([Product]) as products from [dbo].[LITA_Capstone_Dataset]
where [OrderDate] between '2024-06-01' and '2024-10-01'
group by [Product]);

------products sold in the last quarter
select [Product] as products, count([OrderDate]) as orders from [dbo].[LITA Capstone Sales Data Dataset]
where [OrderDate] between '2024-06-01' and '2024-10-01' 
group by [Product]
```
Excel
```Excel
Revenue: =F2*G2
Average sales by product: =AVERAGEIF($C$2:$C$9922,C7,$F$2:$F$9922)
Total Revenue by region: =SUMIF($D$2:$D$9922,D8,$H$2:$H$50001)
```
PowerBI
```PowerBi
Revenue = 'LITA Capstone Sales Data Dataset'[Quantity] * 'LITA Capstone Sales Data Dataset'[UnitPrice]
```

### Data Visualization
Pivot table
![Screenshot (21)](https://github.com/user-attachments/assets/12036754-4008-4222-93ca-ec4bdf75cf30)


Powerbi Dashboard
![Screenshot (19)](https://github.com/user-attachments/assets/7036ba5d-b838-418c-805f-207bc82e9bbc)

### Observation from Visualizations
Looking at the sales for each clothing item, hats were the most sold with 15929 of them sold and jackets were the least sold with only 5452 sold. Most sales were done in the South region with a total of 24298 items sold in the South. The West region sold least items with 11,400 items sold in all. Looking through the sales sold in the year, most goods were sold in Febraury and there is a massive decline in sales in November, May and December with sales of 2970,2482 and 2465 respectively. The highest revenue was brought in by the south region with a total revenue of 0.93Million and the least revenue was brought in by the West region with revenue of 0.3Million.

The clothing item that brought in the most revenue is Shoe with a total revenue of 613,380 which is because of the higher price of the shoes. The item that brought the least revenue is socks. The are top 500 customers based on purchase amount  with purchase amount of 4,235 each. The products not sold in the last quarters were shirt, socks and jackets, This proves that jackets are not really sold. 

In the South, gloves are mostly sold with 9900 pieces sold closely followed by shoes with 9000 sold and jackets are not sold at all. In the East, hats are mostly sold with 6900 sold. In the North, Shirts are mostly sold with 6400 sold. In the west, socks are mostly sold with 3500 pieces sold. 

### Recommendation from Analysis
Hats should be kept more in the stores as they are mostly sold and jackets should be the least stocked. Awareness should be done the public as regards other products that are available. Posters with "Jackets are also available' should be made to drive customers' request.

More advertisement should be targetted to the West region to increase sales in the West.
Gloves and shoes should be in high quantity in the south. Hats should also be in high quantity in the East and shirts readily available in the North.

The top 500 customers should be given coupons or discounts to encourage more purchase from them




