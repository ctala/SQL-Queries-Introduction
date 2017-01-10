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
