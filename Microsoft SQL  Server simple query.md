# Microsoft SQL  Server simple query

- ### Add a new primary key column that automatically increments for your existing data
1. **Add the New Primary Key Column with Identity:**
```
ALTER TABLE users
ADD id INT IDENTITY(1,1) PRIMARY KEY;
```
In this example, INT is the data type of the column, and IDENTITY(1,1) specifies that the column will start at 1 and increment by 1 for each new row. We've also set this column as the primary key.

2. **Verify the Changes:**

```
SELECT id FROM users;
```
The id column will now automatically generate unique incrementing values for each row in your existing data.

- ### force import of a database regardless of constrained and foreign key
```
-- Disable foreign key checks
SET FOREIGN_KEY_CHECKS = 0;

-- Import data
-- Your import statements go here

-- Enable foreign key checks
SET FOREIGN_KEY_CHECKS = 1;
```
