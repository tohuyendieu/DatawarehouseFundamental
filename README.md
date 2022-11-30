# DatawarehouseFundamental
1. Context
Suppose that you are an employee of a large company that sells bicycles and cycle accessories. This 
company has sales in Canada, the United States and in various Spanish-speaking countries in South 
America such as Mexico. The diagram the operational base is too large to print on a page A4, you could 
create a database diagram in your SSMS to view the operational base. The operational base is divided into 
several schemas (Sales, Person,Production ...), each corresponding to a specific operational need. Note 
that:
- The SalesOrderHeader table contains general information about customer orders; The 
CurrencyRateID = NULL corresponding to order paid in USD.
- The SalesOrderDetail table contains the details of the products sold.
- The SalesTerritory table contains geographic information about customers. It also serves to 
identify the geographical areas covered by the company (although this is not what interests us 
here).
- The Customer table contains the customer information. The customers can be of two types: "I" 
(individual customers) or "S" (store). Note that you have also a list of old customers provided in 
the file Customers.xls. There could have some customers that appear both in the Customer table 
and in the excel file.

2. Business Requirement 
The marketing department wants to increase the volume of online sales. For this, it is necessary to better 
describe and understand the way in which these sales work. We will focus on the secondary Customer 
Relationship Management flow: knowledge of individual customers - Marketing tools.
Your goal is to build a datamart regarding sales made to individual customers (INDIVIDUAL). We do not 
consider here sales made for professional customers (store), moreover these stores get their supplies
directly from a commercial, as you can see in the diagram operational. Your analysis should focus on 
orders that have already been delivered to individual customers.
Your analysis must relate to the products: their characteristics (category, subcategory, model ...), their 
cost, etc ... In fact, we are not interested in each product, but in each group of products of the same color, 
standardCost, ListPrice, Size, SizeUnitMeasure, Weight, WeightUnitMeasure, ProductLine, Class, Style, 
Category, Subcategory, Model. Note that the decision makers do not want to analyze the sales for each 
precise price, cost or weight but they want to analyze the sales according to each price range (0-100, 100-
200, 200-300, …, 900-1000, 1000-2000, 2000-3000, 3000-4000, > 4000), to each cost range (0-100, 100-
200, 200-300, …, 900-1000, 1000-2000, 2000-3000, 3000-4000, > 4000) and to each weight range (0-50, 
50-100, 100-150, 150-200, 200-250, 250-300, > 300).
We are interested also in the geographic area where the sale took place (SalesTerritoryRegion (Name 
attribute in SalesTerritory table), SalesTerritoryCountry (note that in the data warehouse, we are 
interested in the country region name, not the CountryRegionCode), and SalesTerritoryGroup), as well as 
the promotions (Special offer) used by customers during their orders. Promotions are in the form of 
percentages of reduction. The promotion can be some types, it specifies a minimum and maximum 
number of products purchased (MinQty and MaxQty), and has time limits (StartDate and EndDate).
Your analysis should also look at the dates the client has ordered products (OrderDate), on the dates that 
these orders should have been delivered (i.e. the DueDate that was communicated to the customer at his 
request), and the dates on which the order was delivered to them (ShipDate). Indeed, long waiting times 
between the order and the delivery or if the customer has to wait much longer than what was announced 
when ordering, this can have a very negative impact on future sales for this client, which could prefer to 
go to a competitor's store in the future rather than continue to place his internet orders in our society.
Customers (title, gender, etc.) are of particular interest to you. In this project, you will also create 
customer profiles to help members of the marketing department in the implementation of targeted 
marketing. Decision makers of the marketing department have explicitly asked to keep all the information
on their clients, namely their surname, first name, "middle name" in the United States), address, city, 
postal code, gender, title, education, occupation, etc.
Your analysis should also follow the currency in which internet sales are made (Euro, US $ ...) and the 
amount paid in that currency, but without going into the detail of exchange rates. Note that in the 
SaleOrderHeaders table, CurrencyRateID = NULL corresponding to order paid in USD.
Of course, the margin will be studied closely, and therefore the costs of the products sold and the amount 
of tax will have to be taken into account. Note that, since this company has sales in Canada, the United 
States and various countries Hispanics in South America such as Mexico, VAT rates may change in function 
of the sale. The price of delivery (freight) will also be taken into account because it will have a direct impact 
on the margin, obviously.
