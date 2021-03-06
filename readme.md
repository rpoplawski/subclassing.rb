Learning SQL

1)How many users are there?

SELECT COUNT * FROM users;
50

2)What are the 5 most expensive items?

SELECT title, price FROM items ORDER BY price DESC LIMIT 5;
title|price
Small Cotton Gloves|9984
Small Wooden Computer|9859
Awesome Granite Pants|9790
Sleek Wooden Hat|9390
Ergonomic Steel Car|9341

3)What's the cheapest book? (Does this change for "category is exactly 'book' versus category contains 'book'"?)

The answer to the above question varies depending on how the query is entered.

SELECT title, price, category FROM items WHERE category = 'book' ORDER BY price ASC LIMIT 1;
sqlite> SELECT title, price, category FROM items WHERE category = 'books' ORDER BY price ASC LIMIT 1;
sqlite> SELECT title, price, category FROM items WHERE category like '%book%' ORDER BY price ASC LIMIT 1;
title|price|category
Ergonomic Granite Chair|1496|Books
sqlite> SELECT title, price, category FROM items WHERE category = 'Books' ORDER BY price ASC LIMIT 1;
title|price|category
Ergonomic Granite Chair|1496|Books
sqlite> SELECT title, price, category FROM items WHERE category like '% book%' ORDER BY price ASC LIMIT 1;
title|price|category
Small Cotton Hat|1727|Beauty & Books
sqlite> SELECT title, price, category FROM items WHERE category like '% book %' ORDER BY price ASC LIMIT 1;

Basically, the cheapest book is "Ergonomic Granite Chair" at 1496

4)Who lives at “6439 Zetta Hills, Willmouth, WY”? Do they have another address?
Corrine Little  2 addresses
SELECT first_name, last_name FROM users WHERE id = 40;

SELECT * from addresses WHERE user_id = 40;
id|user_id|street|city|state|zip
43|40|6439 Zetta Hills|Willmouth|WY|15029
44|40|54369 Wolff Forges|Lake Bryon|CA|31587

5)Correct Virginie Mitchell’s address to “New York, NY, 10108”.
The addresses have been adjusted.

6)How much would it cost to buy one of each tool?
SELECT sum(price) FROM items WHERE category = 'Tools';
7383

7)How many total items did we sell?
SELECT sum(quantity) FROM orders;
2125

8)How much was spent on books?
SELECT sum(price) FROM items WHERE category = 'Books';
sum(price)
22702

9)Simulate buying an item by inserting a User for yourself and an Order for that User.
I added a new user with a made-up address with id=55 and user_id= 51
55|51|123 Abc Street|Austin|TX|78734
