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

> These can not be **unsigned**.

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

## MySQL Keys

> `SHOW INDEX FROM table_name;`syntax is used to check keys associated with `table_name`.

### Unique Key

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

#### Drop Unique Key

- `ALTER TABLE` Statement is used to drop the unique key from the table.

```sql
-- Syntax
ALTER TABLE table_name DROP INDEX constraint_name;
-- Example
ALTER TABLE users DROP INDEX user_id_key;
```

### Foreign Key

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

#### foreign_key_checks

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
