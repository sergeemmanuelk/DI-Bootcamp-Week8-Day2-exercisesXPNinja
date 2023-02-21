<!-- Fetch the last 2 customers in alphabetical order (A-Z) – exclude ‘id’ from the results.-->
SELECT first_name, last_name 
FROM customers 
ORDER BY last_name DESC 
LIMIT 2;


<!-- Use SQL to delete all purchases made by Scott. -->
DELETE FROM purchases 
WHERE customer_id = (
  SELECT id 
  FROM customers 
  WHERE first_name = 'Scott'
);

![](cap1.png)

<!-- Does Scott still exist in the customers table, even though he has been deleted? Try and find him. -->
SELECT * FROM customers 
WHERE first_name = 'Scott';

<!-- Use SQL to find all purchases. Join purchases with the customers table, so that Scott’s order will appear, although instead of the customer’s first and last name, you should only see empty/blank. (Which kind of join should you use?). -->

SELECT p.id, p.customer_id, p.item_id, p.quantity_purchased, c.first_name, c.last_name
FROM purchases p
RIGHT JOIN customers c ON c.id = p.customer_id ;

![](cap2.png)


<!-- Use SQL to find all purchases. Join purchases with the customers table, so that Scott’s order will NOT appear. (Which kind of join should you use?) -->

SELECT p.id, p.customer_id, p.item_id, p.quantity_purchased, c.first_name, c.last_name 
FROM purchases p
INNER JOIN customers c ON c.id = p.customer_id;

![](cap3.png)
