# Creating Database & SQL Querying
This hands-on guide will teach you how to create a new database and perform SQL querying.

- [Creating Database & SQL Querying](#creating-database--sql-querying)
  - [1.0 Creating database using psql](#10-creating-database-using-psql)
    - [1.1: Run psql](#11-run-psql)
    - [1.2: Create a database](#12-create-a-database)
    - [1.3: List available databases](#13-list-available-databases)
    - [1.4: Switch database connection](#14-switch-database-connection)
    - [1.5: Reconnect database](#15-reconnect-database)
  - [2.0 Creating table in SQL](#20-creating-table-in-sql)
    - [2.1: Run SQL Statement in psql](#21-run-sql-statement-in-psql)
    - [2.2: List available tables](#22-list-available-tables)

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

