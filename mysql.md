# MySQL

- **INFORMATION_SCHEMA** provides access to database metadata, information about the MySQL server such as the name of a database or table, the data type of a column, or access privileges.

## Data Types

### Numeric Type

- It includes exact data types (integer,decimal etc.) as well as approximate numeric data types(float, real & double)

#### Integer Type

- It is an **integer data type(written without fraction)**.

| Type      | Storage(bytes) | Minimum Value(Signed) | Minimum Value (Unsigned) | Maximum Value (Signed & Unsigned) |
| --------- | -------------- | --------------------- | ------------------------ | --------------------------------- |
| TINYINT   | 1              | -128                  | 0                        | 127                               |
| SMALLINT  | 2              | -32768                | 0                        | 32767                             |
| MEDIUMINT | 3              | -8388608              | 0                        | 8388608                           |
| INT       | 4              | -2147483647           | 0                        | 2147483647                        |
| BIGINT    | 8              | -9223372036854775808  | 0                        | 9223372036854775808               |

> With **unsigned integer** datatype in a column, it only stores **positive numbers**.

#### Fraction Type

- It contains **fractional part** along with numeric part.

| Type         | Stroage(bytes) | Description                                      |
| ------------ | -------------- | ------------------------------------------------ |
| DECIMAL(m,d) | 1              | m is total digits whereas d is no. of decimals.  |
| FLOAT(m,d)   | 2              | Decimal precision can go to 24 places.(apporx)   |
| DOUBLE(m,d)  | 8              | Decimal precision can go upto 53 places.(approx) |

> They can not be **unsigned**.

#### Boolean Type

| Type    | Description                              |
| ------- | ---------------------------------------- |
| BOOL    | Used for **true** & **false** condition. |
| BOOLEAN | Similar to BOOL                          |

### Date & Time Type

- Used to represent date, time datetime, timestamp & year.

| Type         | Range                                                 | Format                | Size(bytes) |
| ------------ | ----------------------------------------------------- | --------------------- | ----------- |
| DATE         | '1000-01-01' to '9999-12-31'                          | 'yyyy-mm-dd'          | 3           |
| TIME         | '-838:59:59' to '838:59:59'                           | 'HH:MM:SS'            | 3+          |
| DATETIME     | '1000-01-01 00:00:00' to '9999-12-31 23:59:59'        | 'yyyy-mm-dd hh:mm:ss' | 5+          |
| TIMESTAMP(m) | '1970-01-01 00:00:01' UTC to '2038-01-19 03:14:07' TC | 'YYYY-MM-DD HH:MM:SS' | 4+          |
| YEAR(2/4)    | Year value as 2/4 digits                              | Default is 4 digits   | 1           |

### String Type

- Used for holding plain text & binary data(files, images etc.)

| Type             | Maximum Size                  | Explanation                                           |
| ---------------- | ----------------------------- | ----------------------------------------------------- |
| CHAR(size)       | Upto 255 characters           | Size - no. of characters(Fixed-length strings)        |
| VARCHAR(size)    | Upto 255 characters           | Size - no. of characters(Variable-length string)      |
| TINYTEXT(size)   | Upto 255 characters           | Size - no. of characters                              |
| TEXT(size)       | Upto 65,535 characters        | Size - no. of characters                              |
| MEDIUMTEXT(size) | Upto 16,777,215 characters    | Size - no. of characters                              |
| LONGTEXT(size)   | Upto 4,294,967,295 characters | Size - no. of characters                              |
| BINARY(size)     | Upto 255 characters           | Size - no. of binary characters(Fixed-length strings) |
| VARBINARY(size)  | Upto 255 characters           | Size - no. of characters (Variable-length string)     |
| ENUM             |                               |                                                       |
| SET              |                               |                                                       |

### BLOB(Binary Large Object) Type

- It holds a variable amount of data.

| Type       | Size                           |
| ---------- | ------------------------------ |
| TINYBLOB   | Upto 255 bytes                 |
| BLOB(size) | Upto 65,535 bytes              |
| MEDIUMBLOB | Upto 16,777,215 bytes          |
| LONGBLOB   | Upto 4,294,967,295 bytes (4GB) |

### Spatial Type

### JSON Type

## Variables

- Variables are used for storing data/information & using throughout the program.
- In MySQL, variables are used in **3** different ways:-
  1. User-Defined Variable
  2. Local Variable
  3. System Variable

#### User-Defined Variable

- **SET** & **SELECT** statement are used to declare & initialize a variable.
- It starts with **@** symbol & can be a maximum of **64 characters** in length.
- variable can store data of types **integer, float, decimal, string** or **NULL**.
- **Syntax**

```sql
-- either '=' or ':=' assignment operator can be used.
-- Using SET Statement
SET @var_name=value;
-- Using SELECT Statement
SELECT @var_name:=value;

-- Examples
SET @age=35.5;
SELECT @name:='Rahul Kumar';

-- To Display the value
SELECT @name;
```

> Accessing **undeclared** variable will give **NULL** output.

#### Local Variable

- It is not prefixed by **@** symbol and it is strongly typed variable(we have to mention type of data variable will store).
- **DECLARE** keyword is used along with **DEFAULT** clause to specify the local variable & if it **DEFAULT** clause is not provided then initial value is **NULL**.
- The scope of local variable is `BEGIN...END` block.

```sql
-- Syntax
DECLARE variable_name datatype(size) DEFAULT default_value;

-- Example
DECLARE total_price Oct(8,2) DEFAULT 0.0;
DECLARE a,b,c INT DEFAULT 0;
```

#### System Variable

- Contains **predefined** variables related with system configuration.
- Each variable has a default value & we can change some system variables using **SET** statement.
- system variables are mainly _GLOBAL_, _SESSION_ or _MIX_ types.

```sql
-- To check current values of variables
SHOW VARIABLES;
SELECT @@var_name;

-- Examples
SHOW VARIABLES LIKE '%version%';
SELECT @@version;
```

## MySQL User

- When MySQL server is installed then it has a **ROOT** user only but sometimes we want to give database access to others without granting them full control. In this situation, we create a non-root user & grant them specific privileges to access & modify the database.
- To get information about current user, we user either `SELECT user();` or `SELECT current_user();`.
- To see the currently logged user, we use `SELECT user,host,db,command FROM information_schema.processlist;`.

#### Create User

- **CREATE USER** statement is used to create a new user account in the database server.
- After creating a new user account, we have to provide privileges to it & some of these most commonly used privileges are:-
  1. **ALL PRIVILEGES**
  1. **CREATE**
  1. **DROP**
  1. **DELETE**
  1. **INSERT**
  1. **SELECT**
  1. **UPDATE**

```sql
-- Syntax for Creating new user(account_name --> <username>@<hostname> || <username>@%)
CREATE USER [IF NOT EXISTS] account_name IDENTIFIED BY 'password';
-- Syntax for granting privileges
GRANT <privilege> ON *.* TO account_name;

-- Examples
CREATE USER rahul@localhost IDENTIFIED BY 'rahulkumar124';
GRANT ALL PRIVILEGES ON *.* TO rahul@localhost;
-- Limited Privileges

GRANT SELECT,UPDATE,INSERT ON *.* TO rahul@localhost;
```

- To check for existing privileges of an user,

```sql
-- syntax
SHOW GRANTS FOR username;
-- Example
SHOW GRANTS FOR rahul@localhost;
```

> `SELECT user FROM mysql.user;` returns all users in current MySQL server.

#### Drop User

- **DROP USER** statement lets us to delete one/more user accounts & their privileges from the database server.

```sql
-- Syntax
DROP USER account_name1,...,account_nameN;

-- Example
DROP USER rahul@localhost;
DROP USER rahul@localhost, ram@localhost;
```

#### Change User Password

- To change password of an user account, we can use any of below mentioned ways:-

  1. **UDPATE** Statement
  1. **SET PASSWORD** Statement
  1. **ALTER USER** Statement

- We must have the **UPDATE** privilege for changing the other account password.
- With **UPDATE** statement, we also have to use **FLUSH PRIVILEGES** statement after executing it for reloading privileges from the grant table of MySQL database.
- **SET PASSWORD** statement uses the user account in the **username@localhost** format.
- **ALTER USER** statement with **IDENTIFIED BY** clause is also used for changing password.

```sql
-- Syntax
UPDATE user SET authentication_string = PASSWORD('<password>') WHERE user='<username>' AND host='<hostname>';
FLUSH PRIVILEGES;
-- Example
UPDATE user SET authentication_string = PASSWORD('helloworld') WHERE user='rahulbaran' AND host='localhost';
FLUSH PRIVILEGES;

-- Syntax
SET PASSWORD FOR <username>@<host> = '<password>';
-- Example
SET PASSWORD FOR rahulbaran@localhost = '123455';

-- Syntax
ALTER USER <username>@<host> IDENTIFIED BY '<password>';
-- Example
ALTER USER rahulbaran@localhost IDENTIFIED BY 'Sharma12345';
```

## MySQL Database

### Create Database

- A database is like a directory that stores all files in form a table.
- **charaset_name** is the name of character set to store every character in a string.

```sql
-- Syntax
CREATE DATABASE [IF NOT EXISTS] database_name [CHARACTER SET charset_name] [COLLATE collation_name];
-- Example
CREATE DATABASE college CHARACTER SET utf8mb4;
```

> `SHOW CHARACTER SET;` returns all the character set available.
> `SELECT schema_name FROM information_schema.schemata;` returns all the schema available in current mysql server.

### Drop Database

- We can any of below syntax to drop a database:-
  1. `DROP DATABASE [IF EXISTS] <database_name>;`
  2. `DROP SCHEMA [IF EXISTS] <database_name>;`

### Copy Database

## Table & Views

### ALTER Table

- **ALTER** statement is used for adding,deleting & modifying a table or any table field.
- The statement is always used with **ADD**, **DROP** & **MODIFY** commands.

#### ADD column(s)

```sql
-- Syntax
-- FIRST | AFTER columns_name tells MySQL position of column
ALTER TABLE table_name ADD new_column_name column_definition [FIRST|AFTER column_name], ADD new_column_name column_definition [FIRST|AFTER column_name], ... ;
-- Example
ALTER TABLE players ADD player_name VARCHAR(255) NOT NULL FIRST, ADD age TINYINT UNSIGNED NOT NULL COMMENT 'Player Age' AFTER id;
```

#### Modify column

```sql
-- Syntax
ALTER TABLE table_name MODIFY column_name column_definition [FIRST|AFTER column_name];
-- Example
ALTER TABLE players MODIFY player_name VARCHAR(255) NOT NULL COMMENT 'Name of Player' FIRST;
```

#### Drop column

```sql
-- Syntax
ALTER TABLE table_name DROP COLUMN column_name;
-- Example
ALTER TABLE players DROP COLUMN registration_on;
```

#### Rename column

```sql
-- Syntax
ALTER TABLE table_name CHANGE COLUMN old_name new_name
column_definition [FIRST|AFTER column_name];
-- Example
ALTER TABLE players CHANGE COLUMN age player_age TINYINT UNSIGNED NOT NULL;
```

#### Rename table

```sql
-- Syntax
ALTER TABLE table_name RENAME TO new_table_name;
-- Example
ALTER TABLE players RENAME TO indian_players;
```

### Truncate Table

- **TRUNCATE** statement(part of DDL) removes the complete data from a table without removing its structure.
- It is more efficent as compared to **DELETE** statement since it removes the table internally & recreates it instead of deleting single record at a time.
- We can't use **WHERE clause** with it.
- It can't be used with a table referenced by a **foreign key** or particpated in an **indexed view**.
- To perform **TRUNCATE** operation for the table referenced by **foreign key**, we can first **disable foreign key** checks.

```sql
-- Syntax
TRUNCATE [TABLE] table_name;
-- Example
TRUNCATE TABLE users;

-- Table with Foreign key
SET FOREIGN_KEY_CHECKS = 0;
TRUNCATE TABLE users;
SET FOREIGN_KEY_CHECKS = 1;
```

## MySQL Keys

> `SHOW INDEX FROM table_name;`syntax is used to check keys associated with `table_name`.

#### Unique Key

- It is a single field or combination of fields which ensure that column doesn't store **duplicate values**.
- It can store single **null** value.
- **Syntax**

```sql
-- Using only one column
CREATE TABLE table_name(
    column_name datatype UNIQUE
    ...
);
-- Using more than one column
CREATE TABLE table_name(
    col1 datatype,
    colo2 datatype,
    ...
    CONSTRAINT constraint_name
    UNIQUE(column_names)
);
-- Using ALTER TABLE Statement
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE(column_list);
```

##### Drop Unique Key

- `ALTER TABLE` Statement is used to drop the unique key from the table.

```sql
-- Syntax
ALTER TABLE table_name DROP INDEX constraint_name;
-- Example
ALTER TABLE users DROP INDEX user_id_key;
```

#### Foreign Key

- Used to link one or more table(s) together.
- Also known as **referencing key**.
- **foreign key** field on one table(child table) matches the **primary key** field of another table(parent table).
- It can be defined in two ways:
  - Using `CREATE TABLE` Statement
  - Using `ALTER TABLE` Statement
- **Syntax**

```sql
CONSTRAINT constraint_name
FOREIGN KEY (foreign_key_name),
REFERENCES parent_table_name(col_name)
ON DELETE referenceOption -- SET NULL/CASCADE/RESTRICT/NO ACTION
ON UPDATE referenceOption;
```

- **Example**

```sql
CREATE TABLE users(
    user_id INT NOT NULL auto_increment,
    username VARCHAR(255) NOT NULL UNIQUE COMMENT 'Username of Current User',
    PRIMARY KEY(user_id)
);

CREATE TABLE posts(
    post_id INT
)
```

- To drop an existing **foreign key**, we use `ALTER TABLE` statement.

```sql
-- Syntax
ALTER TABLE table_name DROP FOREIGN KEY fk_constraint_name;
-- Example
ALTER TABLE posts DROP FOREIGN KEY user_id_fk;
```

##### foreign_key_checks

- It is a special variable to control the **foreign key** checking into the tables.
- By default, it is enabled to enforce the referential integrity.
- Sometimes, we need to disable foreign key checking:
  - We drop a table that is reference by the foreign key.
  - We use `ALTER TABLE` statement on that which has a foreign key.

```sql
-- Disable
SET foreign_key_checks=0;
-- Enable
SET foreign_key_checks=1;
```

## Comments

- To add/change a table comment following command is used:-

```sql
-- Syntax
ALTER TABLE <tablename> COMMENT="<commented text>";
-- Example
ALTER TABLE users COMMENT='Hello new table';
```

- To add a comment in a column we use `COMMENT` command with _comment message_.

```sql
CREATE TABLE users (
    user_id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(40) NOT NULL,
    username VARCHAR(20) NOT NULL UNIQUE COMMENT 'username'
);
```

- To check comment of a column we use following command:-

```sql
-- Syntax
SHOW FULL COLUMNS FROM <column_name>;
```

- To change a comment of a column we use `ALTER` Command.

```sql
-- Syntax
ALTER TABLE <tablename> MODIFY COLUMN <column_name> <column_type> COMMENT '<comment_msg>';
-- Example
ALTER TABLE users MODIFY COLUMN username VARCHAR(100) NOT NULL UNIQUE COMMENT 'Your username';
```
