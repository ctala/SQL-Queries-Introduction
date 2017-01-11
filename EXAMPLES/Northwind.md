## Examples using the Northwind Database

###  Aphabetical list (first and last name only) of all Northwind Traders employees

```sql
SELECT FirstName,LastName
FROM Employees
ORDER BY FirstName ASC;
```

### Alphabetical list of all Northwind Traders employees that are not sales representatives.  
Include the employees title.

```sql
SELECT FirstName,LastName, Title FROM Employees
WHERE Title <> "Sales Representative"
ORDER BY FirstName ASC;
```

### Names of all Northwind Traders customers who are based in Brazil.
Include customer id, name, city, and country, sorted by name

```sql
SELECT CustomerID,CompanyName,City,Country FROM Customers
WHERE
Country = "Brazil";
```

### Total number of orders placed by order date.

```sql
SELECT count(*) as "Total Number of Orders",OrderDate
FROM Orders
GROUP BY OrderDate
ORDER BY OrderDate DESC;
```


### Total orders were placed in the first quarter of 1995 (Jan, Feb, and Mar)

```sql
SELECT count(*) as "Total Q1 1995"
FROM Orders
WHERE
OrderDate >= "1995-01-01"
AND
OrderDate <= "1995-03-31";
```

### Quantity of orders by customer

```sql
SELECT CustomerID, count(*) as "Total Orders "
FROM Orders
GROUP BY CustomerID;
```

### Orders by employee including last name

```sql
SELECT Employees.LastName, count(*) as Total
FROM Orders, Employees
WHERE
Orders.EmployeeID = Employees.EmployeeID
GROUP BY Employees.LastName
ORDER BY Total DESC;
```

### Units in stock for each product of available products.

```sql
SELECT ProductName,UnitsInStock FROM Products
WHERE
Discontinued = 0
Order By ProductName;
```

### Total units sold and total sales before a discount of descontinued products

```sql
SELECT Products.ProductID, ProductName,
SUM(OD.Quantity) as "Total Units Sold" ,
 OD.UnitPrice*OD.Quantity as "Total Sales"
FROM Products, "Order Details" as OD
WHERE
OD.ProductID = Products.ProductID
AND
Products.Discontinued = 1
GROUP BY Products.ProductID
;
```


### Orders by day shipped by United Package in 1994.
Show a report that includes Company Name, Shipped Date, and numbers of orders by ship
date for this company.



For each customer, how many UNIQUE orders were placed, what was the total sales before
a discount (Unit Price * Quantity), total discounts given to each customer, and total sales
after the discount.
