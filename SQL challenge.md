
**/*Which customers are from the UK?*/

select customername from customers
where country = 'UK';

Result:
Number of Records: 7
CustomerName
Around the Horn
B's Beverages
Consolidated Holdings
Eastern Connection
Island Trading
North/South
Seven Seas Imports

**/*What is the name of the customer who has the most orders?*/

SELECT customername, Count(*) AS CountVal FROM orders
JOIN customers ON customers.customerid = orders.customerid
GROUP BY customername
ORDER BY CountVal DESC
LIMIT(1)

Result:
Number of Records: 1
CustomerName	CountVal
Ernst Handel	10

**/*Which supplier has the highest average product price?*/

SELECT suppliername, avg(price) AS averagePrice FROM suppliers
JOIN products ON Products.supplierid = suppliers.supplierid
GROUP BY suppliername
ORDER BY averageprice desc
LIMIT(1)

Result:
Number of Records: 1
SupplierName	averagePrice
Aux joyeux ecclésiastiques	140.75

**/*How many different countries are all the customers from? (Hint: consider DISTINCT.)*/

select count(distinct country) from customers

Result:
Number of Records: 1
count(distinct country)
21

**/*What category appears in the most orders?*/

SELECT CategoryName, count(*) as countval FROM products
JOIN Categories ON Products.CategoryID = Categories.CategoryID
join orderdetails on products.productid = orderdetails.productid
GROUP BY CategoryName
ORDER BY CountVal DESC
limit(1);

Result:
Number of Records: 1
CategoryName	countval
Dairy Products	100

**/*What was the total cost for each order?*/

select orders.orderid ,quantity*price as totalcost from orders 
join orderdetails on orderdetails.orderid = orders.orderid join
products on products.productid = orderdetails.productid
group by orders.orderid
limit(5)

Result:
Number of Records: 5
OrderID	totalcost
10248	174
10249	2120
10250	315.75
10251	421
10252	1360


**/*Which employee made the most sales (by total cost)?*/

select employees.employeeid,lastname,firstname, quantity*price as totalcost from employees
join orders on orders.employeeid = employees.employeeid
join orderdetails on orderdetails.orderid = orders.orderid
join products on products.productid = orderdetails.productid
group by employees.employeeid 

Result:
Number of Records: 9
EmployeeID	LastName	FirstName	totalcost
1	Davolio	Nancy	500
2	Fuller	Andrew	62.46
3	Leverling	Janet	1020
4	Peacock	Margaret	2565
5	Buchanan	Steven	954
6	Suyama	Michael	300
7	King	Robert	240
8	Callahan	Laura	547.2
9	Dodsworth	Anne	495

**/*Which employees have BS degrees? (Hint: look at the LIKE operator.)*/

select * from employees
where notes  LIKE '%bs%'

Result:
Number of Records: 2
	LastName	FirstName	BirthDate	Photo	Notes
3	Leverling	Janet	1963-08-30	EmpID3.pic
5	Buchanan	Steven	1955-03-04	EmpID5.pic

**/*Which supplier of three or more products has the highest average product price? (Hint: look at the HAVING operator.)*/

select suppliername , avg(price) as avgPrice, count(productid) as totalProducts from products
join suppliers on suppliers.supplierid = products.supplierid
group by suppliers.supplierId
having count(productid) > 2
order by avgPrice desc
limit(1)

Result:
Number of Records: 1
SupplierName	avgPrice	totalProducts
Tokyo Traders	 46         3
