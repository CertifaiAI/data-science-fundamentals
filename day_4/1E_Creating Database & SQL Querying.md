# Creating Database
This hands-on guide will teach you how to create a new database and perform SQL querying.

- [Creating Database](#creating-database)
  - [1.0 Creating database using psql](#10-creating-database-using-psql)
    - [1.1: Run psql](#11-run-psql)
    - [1.2: Create a database](#12-create-a-database)
    - [1.3: List available databases](#13-list-available-databases)
    - [1.4: Switch database connection](#14-switch-database-connection)
    - [1.5: Reconnect database](#15-reconnect-database)
  - [2.0 Creating table in SQL](#20-creating-table-in-sql)
    - [2.1: Run SQL Statement in psql](#21-run-sql-statement-in-psql)
    - [2.2: List available tables](#22-list-available-tables)
- [SQL Querying](#sql-querying)
  - [1.0 `CREATE TABLE`](#10-create-table)
  - [2.0 `INSERT`](#20-insert)
  - [4.0 `SELECT`](#40-select)
  - [3.0 `UPDATE`](#30-update)
  - [5.0 `DELETE`](#50-delete)
  - [6.0 `JOIN`](#60-join)
  - [7.0 `DROP`](#70-drop)

## 1.0 Creating database using psql
### 1.1: Run psql

Run the command below and enter the password for the `postgres` database user if prompts.

**Windows command:**
```console
psql -d postgres -U postgres -W
```

**Ubuntu command:**
```console
sudo -u postgres psql
```

**Example output:**
```
D:\>psql -d postgres -U postgres -W
Password:
psql (13.4)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

postgres=#
```

`postgres=#` indicates that you are connected to the default database which is the `postgres` database.

For Windows users, you can ignore the WARNING message displayed here. If you want to resolve this WARNING, you can run `chcp 1252` before running psql.

**Solution:**
```
C:\WINDOWS\system32>chcp 1252
Active code page: 1252

C:\WINDOWS\system32>psql -d postgres -U postgres -W
Password:
psql (13.4)
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

postgres=#
```

### 1.2: Create a database

Use the SQL statement below to create a new database with the name `practice_1`.

**SQL:**
```SQL
CREATE DATABASE practice_1;
```

**Example output:**
```
postgres=# CREATE DATABASE practice_1;
CREATE DATABASE
```

### 1.3: List available databases

You can run the command below in psql to show all the available databases in your PostgreSQL.

**psql Command:**
```console
\l
```

**Example output:**
```
postgres=# \l
                              List of databases
    Name    |  Owner   | Encoding | Collate |  Ctype  |   Access privileges
------------+----------+----------+---------+---------+-----------------------
 postgres   | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
 practice_1 | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
 template0  | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +
            |          |          |         |         | postgres=CTc/postgres
 template1  | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +
            |          |          |         |         | postgres=CTc/postgres
(4 rows)
```

`\l` is not a SQL statement here, it is one of the meta-commands that can be used in psql.

You will see the newly created database named `practice_1` if you successfully run the previous create database SQL statement. There are also 3 more existing databases that have been created beforehand. 

`postgres`: A default database meant for use by users, utilities and third-party applications. Any connection without specifying other databases will automatically connect to this database.

`template1`: A template database that will be used to create another new database. When creating a new database, the inner structure of `template1` will be copied to that new database.

`template0`: A backup template database that is used to restore the `template1` database if damaged or altered.


### 1.4: Switch database connection

Now you will use the command below to switch the connection to the new `practice_1` database created previously.

**psql Command:**
```console
\c practice_1
```

**Example output:**
```
postgres=#  \c practice_1
Password:
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
You are now connected to database "practice_1" as user "postgres".
practice_1=#
```

`practice_1=#` terminal prompt indicates that you are currently connected to the `practice_1` database.

### 1.5: Reconnect database

Next time when you want to reconnect to the created database in psql, you can use the command below.

**psql Command:**
```console
psql -d practice_1 -U postgres -W
```

**Example output:**
```
D:\>psql -d practice_1 -U postgres -W
Password:
psql (13.4)
Type "help" for help.

practice_1=#
```

## 2.0 Creating table in SQL

### 2.1: Run SQL Statement in psql

Paste the SQL statement below in the psql terminal and hit `Enter`. This SQL statement will create a SQL table in the `practice_1` database.

**SQL:**
```SQL
CREATE TABLE country
(
  country_id INTEGER,
  country_name VARCHAR(50) NOT NULL,
  country_code VARCHAR(2) UNIQUE NOT NULL,
  population INTEGER,
  gdp NUMERIC(5, 2),
  PRIMARY KEY (country_id)
);
```

**Example output:**
```
practice_1=# CREATE TABLE country
practice_1-# (
practice_1(#   country_id INTEGER,
practice_1(#   country_name VARCHAR(50) NOT NULL,
practice_1(#   country_code VARCHAR(2) UNIQUE NOT NULL,
practice_1(#   population INTEGER,
practice_1(#   gdp NUMERIC(5, 2),
practice_1(#   PRIMARY KEY (country_id)
practice_1(# );
CREATE TABLE
practice_1=#
```

You can run any SQL statement using psql. Remember to put `;` (semicolon) at the end of each SQL statement.

> Semicolon is the standard way to separate each SQL statement in database systems that allow more than one SQL statement to be executed in the same call to the server.

### 2.2: List available tables

To verify or check existing tables, you can use the command below in psql. It will list out all the available tables created in this database.

**psql Command:**
```Console
\dt
```

**Example output:**
```
practice_1=# \dt
          List of relations
 Schema |  Name   | Type  |  Owner
--------+---------+-------+----------
 public | country | table | postgres
(1 row)
```

From the output result, you can see that the `country` table is created by the `postgres` user (the default database user you are using).

# SQL Querying

## 1.0 `CREATE TABLE`

<!-- **General SQL Syntax:**
```SQL
CREATE TABLE [IF NOT EXISTS] <table_name> (
    <column1> <datatype(length)> <column_constraints...>,
    <column2> <datatype(length)> <column_constraints...>,
    <table_constraints...>
);
``` -->

**SQL:**
```SQL
CREATE TABLE country
(
    country_id INTEGER,
    country_name VARCHAR(50) NOT NULL,
    country_code VARCHAR(2) UNIQUE NOT NULL,
    population INTEGER,
    yearly_change NUMERIC(5, 2),
    PRIMARY KEY (country_id)
);
```

**SQL:**
```SQL
CREATE TABLE IF NOT EXISTS subcountry
(
    subcountry_id INTEGER PRIMARY KEY GENERATED ALWAYS AS IDENTITY,
    country_id INTEGER,
    subcountry_name VARCHAR(100) NOT NULL,
    subcountry_code VARCHAR(2) NOT NULL,
    subcountry_level VARCHAR(100),
    FOREIGN KEY (country_id)
        REFERENCES country(country_id)
);
```

**Example output:**
```
```

<!-- 
https://www.postgresqltutorial.com/postgresql-identity-column/
https://www.postgresqltutorial.com/postgresql-foreign-key/
 -->

## 2.0 `INSERT`

<!-- 
Insert malaysia & indonesia
Insert at least 3 subcountry for both country
https://www.worldometers.info/world-population/population-by-country/
 -->

**SQL:**
```SQL
INSERT INTO country (country_id, country_name, country_code, population, yearly_change)
VALUES (1, 'Malaysia', 'MY', 32365999, 1.30);
```

**SQL:**
```SQL
INSERT INTO country (country_id, country_name, country_code, population, yearly_change)
VALUES
    (2, 'Singapore', 'SG', 5850342, 0.79),
    (3, 'Indonesia', 'ID', 126476461, -0.30);
```

**SQL:**
```SQL
INSERT INTO subcountry (country_id, subcountry_name, subcountry_code, subcountry_level)
VALUES
    (1, 'Johor', '01', 'State'),
    (1, 'Kedah', '02', 'State'),
    (1, 'Kelantan', '03', 'State');
```

**SQL:**
```SQL
INSERT INTO subcountry (country_id, subcountry_name, subcountry_code, subcountry_level)
VALUES
    (3, 'Aceh', 'AC', 'Special Region'),
    (3, 'Bali', 'BA', 'Province'),
    (3, 'Bangka Belitung', 'BB', 'Province'),
    (3, 'Bengkulu', 'BE', 'Province');
```

**Example output:**
```
```

<!-- 
https://www.enterprisedb.com/postgres-tutorials/postgresql-query-introduction-explanation-and-50-examples
https://www.postgresqltutorial.com/postgresql-insert/
https://www.postgresqltutorial.com/postgresql-insert-multiple-rows/
 -->


## 4.0 `SELECT`

<!-- 
Select country table
select subcountry table
select with condition
 -->

**SQL:**
```SQL
SELECT * FROM country;
```

**SQL:**
```SQL
SELECT subcountry_name, subcountry_level
FROM subcountry;
```

**SQL:**
```SQL
SELECT * FROM country
ORDER BY population ASC;
```

**SQL:**
```SQL
SELECT * FROM subcountry
WHERE country_id = 1;
```

<!-- 
https://www.postgresqltutorial.com/postgresql-select/
 -->

## 3.0 `UPDATE`

<!-- 
Update kuala lumpur + population
 -->


**SQL:**
```SQL
UPDATE country
SET population = 273523615,
    yearly_change = 1.07
WHERE country_id = 3
RETURNING *;
```

**SQL:**
```SQL
INSERT INTO subcountry (country_id, subcountry_name, subcountry_code)
VALUES
    (1, 'Melaka', '04'),
    (1, 'Negeri Sembilan', '05'),
    (1, 'Pahang', '06');
```

**SQL:**
```SQL
UPDATE subcountry
SET subcountry_level = 'State'
WHERE country_id = 1
RETURNING *;
```

**Example output:**
```
```

<!-- 
https://www.postgresqltutorial.com/postgresql-update/
https://stackoverflow.com/questions/18936896/updating-multiple-rows-with-different-primary-key-in-one-query-in-postgresql
 -->



## 5.0 `DELETE`

<!-- 
DELETE a subcountry
 -->

**SQL:**
```SQL
DELETE FROM subcountry
WHERE subcountry_name = 'Aceh'
RETURNING *;
```

<!-- 
https://www.postgresqltutorial.com/postgresql-delete/
 -->

## 6.0 `JOIN`
<!-- 
Select join 2 tables
inner join
left join
full join
 -->

**SQL:**
```SQL
INSERT INTO country (country_id, country_name, country_code, population, yearly_change)
VALUES
    (4, 'Japan', 'JP', 126476461, -0.30),
    (5, 'Australia', 'AU', 25499884, 1.18);

INSERT INTO subcountry (subcountry_name, subcountry_code, subcountry_level)
VALUES
    ('Alaska', 'AK', 'State'),
    ('Alabama', 'AL', 'State'),
    ('Arkansas', 'AR', 'State');
```

**SQL:**
```SQL
SELECT subcountry_name, subcountry_level, country_name
FROM subcountry
INNER JOIN country
ON subcountry.country_id = country.country_id;
```

**SQL:**
```SQL
SELECT subcountry_name, subcountry_level, country_name
FROM subcountry
LEFT JOIN country
ON subcountry.country_id = country.country_id;
```

**SQL:**
```SQL
SELECT subcountry_name, subcountry_level, country_name
FROM subcountry
RIGHT JOIN country
ON subcountry.country_id = country.country_id;
```

**SQL:**
```SQL
SELECT subcountry_name, subcountry_level, country_name
FROM subcountry
FULL JOIN country
ON subcountry.country_id = country.country_id;
```

<!-- 
https://www.postgresqltutorial.com/postgresql-joins/
 -->

## 7.0 `DROP`

**SQL:**
```SQL
DROP TABLE subcountry;
```

**SQL:**
```SQL
DROP TABLE country;
```

<!-- 
**General SQL Syntax:**
```SQL
```

**SQL:**
```SQL
```

**Example output:**
```
```
 -->