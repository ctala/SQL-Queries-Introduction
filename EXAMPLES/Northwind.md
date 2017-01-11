## Examples using the Northwind Database

###  Aphabetical list (first and last name only) of all Northwind Traders employees

```sql
SELECT FirstName,LastName
FROM Employees
ORDER BY FirstName ASC;
```

### Alphabetical list of all Northwind Traders employees that are not sales representatives.  Include the employees title.

```sql
SELECT FirstName,LastName, Title FROM Employees
WHERE Title <> "Sales Representative"
ORDER BY FirstName ASC;
```
