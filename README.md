# ATM System | CRUD | JDBC | mySQL Database | 

![](images/ATM-Database-System.jpeg)

This program is a simple ATM system using JDBC (Java Database Connectivity) to interact with a MySQL database.

When the program starts, it connects to the "atm" database using the MySQL JDBC driver, and then prompts the user to enter their PIN number. The PIN number is used as an account number to retrieve the user's account information (name and balance) from the "new_table" table in the database.

If the PIN number is valid and matches an account in the database, the program enters a loop that presents the user with several options: check balance, deposit, withdraw, print receipt, or exit. The user's choice is read from standard input using a Scanner object, and then a switch statement executes the corresponding action.

Overall, this program demonstrates basic database connectivity and CRUD (Create, Read, Update, Delete) operations using JDBC and MySQL, as well as basic user input/output using Scanner and standard input/output streams.

# Code & Algorithm Review 
> Some potenital updates after reviewing the code and logic.

## 1. Use prepared statements
Instead of concatenating the PIN number directly into the SQL query, it's recommended to use a prepared statement. This helps prevent SQL injection attacks and improves performance. For example, instead of `String query = "SELECT * FROM new_table where ac_no=" +pin;`, we can use:
```
String query = "SELECT * FROM new_table where ac_no=?";
PreparedStatement pstmt = connect.prepareStatement(query);
pstmt.setInt(1, pin);
ResultSet rs = pstmt.executeQuery();
```

## 2. NO MAGIC NUMBERS PLEASE.
Instead of using magic numbers in the switch statement, it's recommended to use an enum to represent the user's choice. This makes the code more readable and less error-prone. For example:
```
enum Option {
  CHECK_BALANCE,
  DEPOSIT,
  WITHDRAW,
  PRINT_RECEIPT,
  EXIT
}
...
switch (Option.values()[choice - 1]) {
  case CHECK_BALANCE:
    ...
  case DEPOSIT:
    ...
  case WITHDRAW:
    ...
  case PRINT_RECEIPT:
    ...
  case EXIT:
    ...
}
```

## 3. Tie-up Loose Ends.
Instead of manually closing the database resources, we should use try-with-resources. This ensures that the resources are properly closed even in case of exceptions or errors. For example:
```
try (Connection connect = DriverManager.getConnection("jdbc:mysql://localhost:3306/atm", "root", "Element1991");
     Statement stmt = connect.createStatement();
     Scanner scan = new Scanner(System.in)) {
  ...
} catch (Exception e) {
  ...
}

```















