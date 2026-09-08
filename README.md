# SQL using Python

This repository contains practical exercises for learning and working with **SQL through Python**, primarily using **SQLite** in Jupyter Notebooks.

The goal is to combine Python programming with database operations, allowing SQL concepts to be practiced by creating, populating, querying, and manipulating local databases directly from Python.

## SQLite

**SQLite** is a lightweight, serverless, self-contained relational database system. Unlike database systems that require a separate database server, SQLite stores an entire database in a single `.db` file, making it particularly convenient for learning, experimentation, and small-scale applications.

Python provides the built-in `sqlite3` module for working with SQLite databases. This repository uses it to connect Python code with SQL databases and execute SQL scripts.

## Activating a SQLite Database

The practical exercises use a SQL script such as `setup.sql` to create and populate a database. The following code reads the SQL script, creates a SQLite database file, and executes the script:

```python
import sqlite3
import warnings

warnings.filterwarnings("ignore")

# Load SQL script
with open("setup.sql", "r") as sql_file:
    sql_script = sql_file.read()

# Create and populate the .db file
connection = sqlite3.connect("practice.db")

cursor = connection.cursor()
cursor.executescript(sql_script)

connection.commit()
connection.close()

print("Database file 'practice.db' successfully created!")
```

### How it works

1. **Import `sqlite3`** — Provides Python's interface for working with SQLite.
2. **Load `setup.sql`** — Reads the SQL commands stored in the script.
3. **Create/connect to `practice.db`** — `sqlite3.connect()` creates the database file if it does not already exist.
4. **Create a cursor** — The cursor is used to execute SQL commands.
5. **Execute the SQL script** — `executescript()` runs the SQL statements from `setup.sql`, such as creating tables and inserting data.
6. **Commit the changes** — `commit()` saves the modifications to the database.
7. **Close the connection** — `close()` safely ends the database connection.

Once the database has been created, SQL queries can be executed from the Jupyter Notebook using the SQLite connection and cursor.

## Repository Contents

The notebooks and SQL scripts may cover:

* Creating and populating SQLite databases
* Creating and modifying tables
* Inserting, updating, and deleting records
* Querying databases with `SELECT`
* Filtering, sorting, and grouping data
* Aggregate functions
* Joins and relationships
* Subqueries
* Combining Python and SQL
* Practical SQL exercises using sample databases

More exercises and database examples may be added over time.
