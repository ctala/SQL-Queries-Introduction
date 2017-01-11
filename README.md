# SQL Queries Introduction

We are going to use SQLite as a Database Engine to try the SQL Queries.

## Files attached :
* Northwind.sqlite : The actual database that can be open with any SQLite editor.
* Northwind.Sqlite3.sql : Includes the SQL code to create the Database.

## How to run the database:
The easiest way to run the database is to download the code of this repository and upload the Northwind.sqlite to an online SQLite manager like https://sqliteonline.com/.


##Queries

### Showing Available Tables


#### Query
```sql
SELECT name FROM sqlite_master ;
```


### Showing the content of one table

#### Query to get all the content
```sql
SELECT * FROM Categories;
```

In this case "\*" represents "ALL" fields. Everytime that we just need to get all the columns or fields for all the results or rows we will use asterisk.

#### Query to get specific fields

```sql
SELECT CategoryName,Description FROM Categories;
```

When we just need to get specific fields from the table we must specified which fields do we need. In this case the query will return all the rows but only the columns called Categoryname and Descrition.


#### Limiting the quantity of results

```sql
SELECT CategoryName,Description FROM Categories limit 1;
```

With the last query we will run the same example as before where we got only CategoryName and Description columns, but in this case we will get only one result. We can use any number that we want !

#### Conditioning the results
```sql
SELECT * FROM Customers WHERE ContactName = "Maria Anders";
```
We will use the "Where" clause when we want to condition the output of the results. In this case we will show all the results from the table Customers in which the ContactName is equals to "Maria Anders".

#### Conditioning the results with like.
```sql
SELECT * FROM Customers WHERE ContactName Like "Maria%";
SELECT * FROM Customers WHERE ContactName Like "%Maria%";
SELECT * FROM Customers WHERE ContactName Like "%Maria";
```

With the last examples we can have 3 possible outputs.
* All the customers which name starts with Maria.
* All the customers which name contains Maria.
* All the customers which name finishes with Maria.

#### Multiple Conditioning.

```sql
SELECT *  FROM Customers
WHERE ContactName like "A%"
AND
ContactTitle = "Owner";
```
In this case we are going to obtain all the results of customers on which their name starts with an "A" and their Contact Title is owner. We will introduce as many conditions as we want separated by an "AND".

###  Showing the content from multiple tables.
```sql
SELECT * FROM Orders, Customers
WHERE
Orders.CustomerID = Customers.CustomerID
```

In this case we are getting the results from two different tables, Orders and Customers, and we want to get all the orders and the customer information from those orders. In this case we need to link together both tables. In the orders table we have a field called CustomerID that correspond to the unique ID of the customer, there is only one CustomerID per customer making it unique.

If we don't link together the tables I will have as a result all the possible combinations of customers with all the orders.

### Math Operations on Queries.
#### Counting the results.

```sql
SELECT count(*) FROM Customers;
```




#### Calculate the sum on the results.

```sql
SELECT SUM(Quantity) as "Total Products" FROM "Order Details";
```
In this case we will get the sum of all products in all the orders, so the total quantity of products sold.

#### Calculate the total cost per product in an order
```sql
SELECT OrderID, ProductID, (UnitPrice*Quantity)-(UnitPrice*Quantity*Discount) as ProductTotal FROM "Order Details";
```

In this case we are getting the order id, the product id and the total cost including the discount of the product.


### Everything together

```sql
SELECT OD.OrderID,ProductName, (OD.UnitPrice*OD.Quantity)-(OD.UnitPrice*OD.Quantity*OD.Discount) as ProductTotal
FROM "Order Details" as OD, Products
WHERE
OD.ProductID = Products.ProductID
```

In this case we will get the Total Price quantity of every product per OrderID from The Order Details table and the name of the product from the Products table.


## Examples using the Northwind Database

###  Aphabetical list (first and last name only) of all Northwind Traders employees

```sql
SELECT FirstName,LastName FROM Employees order by FirstName ASC;
```

### Alphabetical list of all Northwind Traders employees that are not sales representatives.  Include the employees title in this report.
