# ATM System | CRUD | JDBC | mySQL Database | 

![](images/.png)

This program is a simple ATM system using JDBC (Java Database Connectivity) to interact with a MySQL database.

When the program starts, it connects to the "atm" database using the MySQL JDBC driver, and then prompts the user to enter their PIN number. The PIN number is used as an account number to retrieve the user's account information (name and balance) from the "new_table" table in the database.

If the PIN number is valid and matches an account in the database, the program enters a loop that presents the user with several options: check balance, deposit, withdraw, print receipt, or exit. The user's choice is read from standard input using a Scanner object, and then a switch statement executes the corresponding action.

For example, if the user chooses to deposit money, the program prompts them to enter an amount, updates the account balance in the database, and then displays the new balance. Similarly, if the user chooses to withdraw money, the program checks if the withdrawal amount is less than or equal to the account balance, updates the balance in the database, and then displays the new balance.

If the user chooses to exit, the program prints a farewell message and terminates. If the PIN number is invalid, the program simply prints an error message and terminates.

Overall, this program demonstrates basic database connectivity and CRUD (Create, Read, Update, Delete) operations using JDBC and MySQL, as well as basic user input/output using Scanner and standard input/output streams.


