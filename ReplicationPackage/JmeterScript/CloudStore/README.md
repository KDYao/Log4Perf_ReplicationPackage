This is the Jmeter load testing script and data for CloudStore. 
We set 150 users accessing the system for 5 hours (30min warmup, 4hour running, 30min cool down). 

1. Set Web Server IP and Port Number in Default HTTP Parameters, please replace the proper parameters according to your testing environment.

2. Read following data:
	users.csv: Read username and password.
	subject.csv: Read subject category of books.
   These data can be accessed from database.


3. Randomly generate Product ID from 1 to 300. This number is flexible according to number of items in database. (For instruction on item generation, please refer to: https://github.com/CloudScale-Project/CloudStore)

4. Randomly generate quantity from 1 to 10. The number is customizable. 

5. Run the HTTP requests: 

	5.1 Loop: 
		General search: /cloudstore/search/ 

	5.2 Loop: 
		Search by author: /cloudstore/search?searchField=author&keyword=
		Search by title: /cloudstore/search?searchField=title&keyword=

	5.3 Loop:
		Check product details: /cloudstore/product-detail?I_ID=${PROD_ID}
		Add to shopping cart: /cloudstore/shopping-cart?&I_ID=${PROD_ID}&QTY=${QUANTITY}&ADD_FLAG=Y
		Extract shopping ID from response body

	5.4 Register using shopping ID: /cloudstore/customer-registration?SHOPPING_ID=${SHOPPING_ID}

	5.5 Fill in customer information for registration
		Extract customer ID from response body

	5.6 Checkout and add payment options.

This iteration will be repeated until total running time exceeds 5 hours.

