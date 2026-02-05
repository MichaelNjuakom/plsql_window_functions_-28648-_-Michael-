# Individual-Assignment-I-SQL-JOINs-Window-Functions-Project #
Demonstrating the practical masteries of: SQL JOINs for multi-table relational analysis and SQL/PL/SQL Window Functions for analytical and business reporting.
# Step 1: Problem Definition #
### Business Context ###
A supermarket operating in the retail industry records its daily sales transactions in its sales department. The supermarket also stores information about customers, products, and purchases in a relational database.The Management of this supermarket wants to use this data to better understand sales performance and customer behavior across different regions in which they are located.
### Data Challenge ###
The supermarket generates a large volume of sales data and this makes it difficult to identify top performing products and understand customer behaviour using simple queries. Management also cannot easily measure how often customers purchase or compare performance across regions and also the time periods in which they buy certain products. More advanced SQL analysis is needed to convert raw data into useful business information.
### Expected Outcome ###
This analysis is expected to help identify top products per region, analyze customer purchasing frequency preferences and behaviour during certain time periods, and also divide customers into groups for targeted marketing and better business decision-making.
# Step 2: Success Criteria #
### Top five products per region or quarter ###
Here, the goal is to Determine the top selling products in each region every month. It can be measurable in that we can count the sales per month in every region, rank them and see which products are doing well in that region.The windows function used here is: RANK()
### Running monthly sales totals ###
Here, the goal is to track the cumulative sales amount for each month and it measurable because it can provide useful in information on the growth of the supermarket as greater output means greater growth and lower output means smaller growth. The windows function used here is: SUM(), OVER()
### Month-over-month growth ###
Here, we compare the sales in one month with the previous month to identify a growth or decline in the supermarket. It is measurable in that, the management can see if sales are increasing or decreasing thus helping with the planning of the supermarket to attain greater growth. The Windows function here is: LAG() / LEAD()
### Customer quartile segmentation ###
The goal here is to divide customers into groups according to their total spending. It measurable in that, it helps identify high value customers for targeted promotions and low value customers for engagement. The windows function is: NTILE(4)
### Three-month moving averages ###
The goal is to see the sales averages over a three month period and to ensure that they are stable. It is measurable in that, it can give a more stable view of trends currently going on and can help in knowing what goods to re-stock the inventory and also making decisions. The windows function used here are  AVG() OVER()
# Step 3: Database Schema Design #
### Sql for the Customer table ### 
create table Customer(Customer_id NUMBER NOT NULL PRIMARY KEY, Fname VARCHAR2(20) NOT NULL, Lname VARCHAR(20) NOT NULL, Region VARCHAR(50), Phone VARCHAR(20),Email VARCHAR2(50))
### Sql for the Products table ###
CREATE TABLE Products (Product_ID NUMBER NOT NULL PRIMARY KEY, Product_Name VARCHAR(20) NOT NULL, Category VARCHAR(20) NOT NULL, Price NUMBER NOT NULL);
### Sql for the Sales table ###
- CREATE TABLE Sales (Sales_ID NUMBER NOT NULL PRIMARY KEY, Customer_id NUMBER NOT NULL, Product_ID NUMBER NOT NULL, Sales_Date DATE, quantity NUMBER, Total_Amount NUMBER)
- ALTER Table Sales ADD Foreign Key(Product_ID) references Products(Product_ID);
- ALTER Table Sales ADD Foreign Key(Customer_ID) references Customer(Customer_ID);

