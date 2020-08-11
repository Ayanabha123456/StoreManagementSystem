# Store Management System
A store management system built using the Java File System, Java JPanel and MySQL database backed up by a recommendation system


# Core Idea
We have created a store management system that is as efficient as possible. It would include functions from 3 perspectives:
-the consumer’s perspective: here we have an android application made in Android Studio that consumers can download on their phones and use to check product inventory and get corresponding bill amount
-the cashier’s perspective: here we have a Java Files + MySQL database where the cashier can generate the bill for consumer’s purchase with the stock being affected accordingly
-the manager’s perspective: Here we have the MySQL database, where the manager will be able to view inventory, modify it and also get a recommendation for adding new items in the proper amount

# Methodology
The software is developed on JAVA IDE. The entire stock of all items is stored in a user-defined file database. The manager is the admin who can update the database on the perspective of stock management. The cashier is the main user of the software who updates the sale of the products involved. This empties the customer cart. The user recommendations of the products are also collected and stored in the database. This gives the store owners an idea of the number of products that need to be purchased as a whole. The recommendation system will implement the multiple regression method, which collects coefficients of regression for each product and suggests the amount of an item that needs to be added to the inventory, based on customer purchase for a particular day, using something called the ‘necessity factor’, which the level of necessity of an item, the manager thinks is required, with arbitrary levels like low, medium and high. To reduce the load on the application, we have implemented the usage of two databases – one is a user-defined file system to store the list of products and manage the cashier accounts, the other is a MySQL database to represent the items of a particular customer being held in a cart and the user reviews. The items are added one by one in a cart and then the cashier has a ‘remove’ option to bill all the items and the final bill is then conveyed to the customer. The following is a description of each of the classes used:

## Intro_Main
This is the main class of the program. The execution starts from here. It prints the opening page which asks the user whether he is a new cashier, an existing cashier or the Manager. Based on the user’s choice, the corresponding class is called. There is also an exit option.

## Sign-In
When we choose 1, it indicates an existing cashier account and we are directed to this class. In this class, user index code, email-id, and password are taken using JOptionPane. These are verified with the existing files in the user-defined file database and if correct, the user is given access to his account. The above fields are entered in the following dialog boxes.



## Account
This is the user’s class. Upon signing in, the user (cashier) is given a few options using a JOptionPane and JButtons as shown below:
 The first option is to add an item to the cart, which asks the user what item to add and in what amount, which is added to the MySQL database. Once a match is found, it shows the remaining stock.
The second option is to remove an item from the cart. This empties the cart and calculates the total bill which is displayed when we select the 5th option which is billing.
The third option shows the items in the cart currently with the name, price and amount.
The fourth option enables the user to search for an item in the store’s inventory, the ‘about us’ option is a credits roll and finally, the cashier can log out from the application once all customers are done. One thing we need to note is that each new transaction begins with the cart database having an empty state

## Sign-Up
In this class, JOptionPane is used to take input about user info and a user account is created. Name, email-id, and password are asked for followed by date of birth. The date of birth is checked with the Calendar class for discrepancy. If everything is inputted correctly, a unique index code is generated which the user has to input along with email-id and password at the time of signing in.
Next after entering the date of birth, the new cashier is given a unique index number.


## Admin
This is the manager’s class. Here the manager is given 3 options- to add/remove inventory, to view inventory and to get recommendation for inventory modification based on store necessity rating. If he chooses the first option, the database is checked for the existence of said item and if found, its quantity can be modified. If not found, a new item entry is created in the database. 



## ListItems
When this class is called, the name, price, and quantity of each product in the store is extracted and printed on the screen for the manager to get an idea about his inventory and cashier to check the inventory during the billing process.

## Recommend
The store system collects manual reviews from the customers at fixed points of a normal business day and stores them in a MySQL database. The ratings are from 0-5. These ratings, once extracted into the class are used to create a regression model based on a customer’s purchase as the dependent variable. The manager inputs the corresponding item code and necessity factor and gets the amount he needs to purchase as part of the recommendation. For a particular item, only that item’s regression coefficient is used in the equation.
