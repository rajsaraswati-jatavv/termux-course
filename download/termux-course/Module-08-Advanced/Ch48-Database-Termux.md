# Chapter 48: Database in Termux

> **Module:** 8 - Advanced  
> **Chapter:** 48 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | SQLite, MySQL, PostgreSQL, Redis, MongoDB |
| Installation Guide | All database systems installation |
| Commands Reference | 30+ database commands |
| Practice Exercises | Hands-on database operations |
| Troubleshooting | Common database issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 48
Title: Database in Termux | SQLite, MySQL, PostgreSQL, MongoDB Complete Guide
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut important hai - Database in Termux!

Agar aap web development kar rahe ho, backend development kar rahe ho,
ya koi bhi application bana rahe ho jo data store karta hai - to
database ka knowledge zaroori hai.

Termux mein aap multiple databases use kar sakte ho - SQLite jo
lightweight hai, MySQL/MariaDB jo popular hai, PostgreSQL advanced
features ke liye, Redis caching ke liye, aur MongoDB NoSQL ke liye.

Ye chapter 20-25 minute ka hai. Isme hum cover karenge:
- SQLite installation aur commands
- MySQL/MariaDB setup
- PostgreSQL installation
- Redis aur MongoDB basics
- CRUD operations
- User management
- Backup aur restore
- Python se database connectivity
- PHP + MySQL integration

To chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe karein.

---

[SECTION 1: DATABASE OVERVIEW - 0:50 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samajhte hain databases kya hote hain aur Termux mein
kaun kaun se databases available hain.

Database ek organized collection of data hai. Jaise aapke phone mein
contacts save hote hain - name, number, email - ye ek simple database
hai. Lekin professionally hum database management systems use karte
hain.

Termux mein ye databases available hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    DATABASES AVAILABLE IN TERMUX                          │
├────────────────┬──────────────┬──────────────────────────────────────────┤
│ Database       │ Type         │ Best For                                 │
├────────────────┼──────────────┼──────────────────────────────────────────┤
│ SQLite         │ Embedded     │ Small apps, mobile, local storage        │
│ MariaDB/MySQL  │ Relational   │ Web apps, CMS, E-commerce                │
│ PostgreSQL     │ Object-Rel   │ Complex apps, GIS, Analytics             │
│ Redis          │ Key-Value    │ Caching, Sessions, Real-time             │
│ MongoDB        │ NoSQL        │ JSON data, Flexible schemas              │
│ LevelDB        │ Key-Value    │ Embedded, High performance               │
└────────────────┴──────────────┴──────────────────────────────────────────┘

SQLite sabse easy hai - no setup, no server, ek file mein sab kuch.
Perfect for learning aur small projects.

MySQL/MariaDB most popular hai web development ke liye - WordPress,
Joomla, Magento sab ise use karte hain.

PostgreSQL advanced features deta hai - JSON support, full-text search,
geographic data, etc.

Redis memory-based hai - super fast, caching ke liye perfect.

MongoDB modern hai - JSON-like documents, flexible schema, great for
rapid development.

Is chapter mein hum in sab ka installation aur basic usage seekhenge.

---

[SECTION 2: SQLITE INSTALLATION & BASICS - 3:00 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye SQLite se shuru karte hain. SQLite already installed aata hai
Termux mein, lekin agar nahi hai to install karein:

    pkg install sqlite -y

SQLite ek command-line tool hai. Direct terminal mein use kar sakte ho:

    sqlite3

Ye SQLite prompt open karega. Exit ke liye:

    .exit

Ab ek database file create karte hain:

    sqlite3 mydb.db

Ye command mydb.db file create karegi agar exist nahi karti. Agar
exist karti hai to use open kar degi.

SQLite prompt mein ye commands use hoti hain:

Database info dekho:
    .databases

Tables list dekho:
    .tables

Schema dekho:
    .schema

Help dekho:
    .help

Format change karo:
    .mode column
    .headers on

Ab ek table create karte hain:

    CREATE TABLE users (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT NOT NULL,
        email TEXT UNIQUE,
        age INTEGER,
        created_at DATETIME DEFAULT CURRENT_TIMESTAMP
    );

Table verify karo:
    .tables
    .schema users

Data insert karo:
    INSERT INTO users (name, email, age) VALUES ('Rahul', 'rahul@email.com', 25);
    INSERT INTO users (name, email, age) VALUES ('Priya', 'priya@email.com', 22);
    INSERT INTO users (name, email, age) VALUES ('Amit', 'amit@email.com', 28);

Data fetch karo:
    SELECT * FROM users;
    SELECT name, email FROM users WHERE age > 23;

Update karo:
    UPDATE users SET age = 26 WHERE name = 'Rahul';

Delete karo:
    DELETE FROM users WHERE name = 'Amit';

Exit:
    .exit

Direct command line se bhi query run kar sakte ho:

    sqlite3 mydb.db "SELECT * FROM users;"

Ye quick queries ke liye useful hai.

---

[SECTION 3: MYSQL/MARIADB INSTALLATION - 7:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Ab MySQL ya MariaDB install karte hain. Termux mein MariaDB milta hai
jo MySQL ka fork hai - fully compatible.

Installation:

    pkg install mariadb -y

Installation ke baad database initialize karna zaroori hai:

    mysql_install_db

Ab MySQL server start karein:

    mysqld_safe &

Ye background mein server start karega. Agar error aaye to permission
check karein ya data directory create karein.

Ab client se connect karein:

    mysql -u root

Default mein root user ka password nahi hota.

MySQL prompt mein:

Current databases dekho:
    SHOW DATABASES;

New database create karo:
    CREATE DATABASE myapp;
    CREATE DATABASE testdb;

Database select karo:
    USE myapp;

Table create karo:
    CREATE TABLE products (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(100) NOT NULL,
        price DECIMAL(10,2),
        stock INT DEFAULT 0,
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    );

Data insert karo:
    INSERT INTO products (name, price, stock) VALUES ('Laptop', 50000.00, 10);
    INSERT INTO products (name, price, stock) VALUES ('Mouse', 500.00, 50);
    INSERT INTO products (name, price, stock) VALUES ('Keyboard', 1500.00, 30);

Query karo:
    SELECT * FROM products;
    SELECT name, price FROM products WHERE price > 1000;

Ab user create karte hain:

    CREATE USER 'appuser'@'localhost' IDENTIFIED BY 'securepass123';
    GRANT ALL PRIVILEGES ON myapp.* TO 'appuser'@'localhost';
    FLUSH PRIVILEGES;

Ye user sirf myapp database ke liye access dega.

MySQL server stop karne ke liye:

    mysqladmin -u root shutdown

Ya phir:

    pkill mysqld

---

[SECTION 4: POSTGRESQL INSTALLATION - 12:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

PostgreSQL ek powerful database hai advanced features ke saath.

Install karein:

    pkg install postgresql -y

PostgreSQL ko initialize karein:

    initdb ~/postgres-data

Server start karein:

    pg_ctl -D ~/postgres-data -l ~/postgres-log start

Ab client connect karein:

    psql

PostgreSQL prompt mein:

Databases list:
    \l

New database:
    CREATE DATABASE analytics;

Connect to database:
    \c analytics

Table with advanced types:
    CREATE TABLE events (
        id SERIAL PRIMARY KEY,
        event_name VARCHAR(100),
        event_data JSONB,
        location POINT,
        created_at TIMESTAMP DEFAULT NOW()
    );

JSON data insert:
    INSERT INTO events (event_name, event_data, location) 
    VALUES ('login', '{"user": "rahul", "device": "mobile"}', POINT(28.6, 77.2));

Query:
    SELECT * FROM events;
    SELECT event_data->>'user' FROM events;

PostgreSQL ke useful commands:
    \dt - tables list
    \d tablename - table structure
    \du - users list
    \q - quit

Server stop:
    pg_ctl -D ~/postgres-data stop

---

[SECTION 5: REDIS INSTALLATION - 15:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Redis ek in-memory data structure store hai. Caching ke liye perfect.

Install:

    pkg install redis -y

Server start:

    redis-server --daemonize yes

Client connect:

    redis-cli

Redis commands:

Set value:
    SET mykey "Hello Termux"
    SET counter 100

Get value:
    GET mykey

Increment:
    INCR counter

Set with expiry (10 seconds):
    SETEX session:abc 10 "user_data"

Check expiry:
    TTL session:abc

List operations:
    LPUSH mylist item1
    LPUSH mylist item2
    LRANGE mylist 0 -1

Hash operations:
    HSET user:1 name "Rahul"
    HSET user:1 email "rahul@email.com"
    HGETALL user:1

Delete key:
    DEL mykey

Check all keys:
    KEYS *

Exit:
    exit

Server stop:
    redis-cli shutdown

---

[SECTION 6: MONGODB INSTALLATION - 17:00 to 19:00]
─────────────────────────────────────────────────────────────────────────────

MongoDB ek NoSQL database hai - JSON-like documents store karta hai.

Note: MongoDB Termux mein directly available nahi hai main repo mein.
Alternatives:

Option 1: Use mongosh (MongoDB Shell) with remote database
    pkg install mongosh -y

Option 2: Use proot-distro with Ubuntu/Debian

Basic mongosh usage:

    mongosh "mongodb://localhost:27017"

Ya remote MongoDB Atlas se connect:
    mongosh "mongodb+srv://cluster.mongodb.net/mydb" --username myuser

MongoDB commands:

Show databases:
    show dbs

Use database:
    use myapp

Insert document:
    db.users.insertOne({
        name: "Rahul",
        email: "rahul@email.com",
        age: 25
    })

Find documents:
    db.users.find()
    db.users.find({age: {$gt: 20}})

Update:
    db.users.updateOne(
        {name: "Rahul"},
        {$set: {age: 26}}
    )

Delete:
    db.users.deleteOne({name: "Rahul"})

---

[SECTION 7: PYTHON DATABASE CONNECTIVITY - 19:00 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Ab Python se databases connect karte hain. Ye real projects mein bahut
useful hai.

SQLite with Python:

    pkg install python -y

Python script:

```python
import sqlite3

# Connect to database
conn = sqlite3.connect('mydb.db')
cursor = conn.cursor()

# Create table
cursor.execute('''
    CREATE TABLE IF NOT EXISTS tasks (
        id INTEGER PRIMARY KEY,
        task TEXT NOT NULL,
        done INTEGER DEFAULT 0
    )
''')

# Insert
cursor.execute("INSERT INTO tasks (task) VALUES (?)", ("Learn Termux",))
conn.commit()

# Query
cursor.execute("SELECT * FROM tasks")
print(cursor.fetchall())

conn.close()
```

MySQL with Python:

    pkg install python mariadb
    pip install mysql-connector-python

```python
import mysql.connector

conn = mysql.connector.connect(
    host='localhost',
    user='root',
    database='myapp'
)
cursor = conn.cursor()
cursor.execute("SELECT * FROM products")
for row in cursor.fetchall():
    print(row)
conn.close()
```

Redis with Python:

    pip install redis

```python
import redis

r = redis.Redis(host='localhost', port=6379)
r.set('mykey', 'myvalue')
print(r.get('mykey'))
```

---

[SECTION 8: BACKUP & SECURITY - 21:30 to 23:30]
─────────────────────────────────────────────────────────────────────────────

Database backup bahut important hai. Har project mein backup strategy
 honi chahiye.

SQLite Backup:
    cp mydb.db mydb_backup.db
    sqlite3 mydb.db ".backup 'backup.db'"

MySQL Backup:
    mysqldump -u root myapp > myapp_backup.sql

MySQL Restore:
    mysql -u root myapp < myapp_backup.sql

PostgreSQL Backup:
    pg_dump mydb > mydb_backup.sql

PostgreSQL Restore:
    psql mydb < mydb_backup.sql

Security Tips:
1. Strong passwords use karein
2. Default users change karein
3. Remote access restrict karein
4. Regular backups lein
5. Sensitive data encrypt karein
6. Least privilege principle follow karein

---

[SECTION 9: SUMMARY & NEXT PREVIEW - 23:30 to 25:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 48 complete! Let's summarize:

✅ SQLite - Lightweight, embedded database
✅ MySQL/MariaDB - Popular relational database
✅ PostgreSQL - Advanced features database
✅ Redis - In-memory caching
✅ MongoDB - NoSQL document store
✅ CRUD Operations - Create, Read, Update, Delete
✅ User Management - Create users, grant permissions
✅ Backup & Restore - Database backup strategies
✅ Python Connectivity - Python se database access
✅ Security Best Practices

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    DATABASE QUICK COMMANDS                                │
├─────────────────────────────────────────────────────────────────────────┤
│ SQLite: sqlite3 mydb.db                                                 │
│ MySQL: mysqld_safe & | mysql -u root                                    │
│ PostgreSQL: pg_ctl start | psql                                         │
│ Redis: redis-server | redis-cli                                         │
│ MySQL Dump: mysqldump -u root db > backup.sql                           │
│ SQLite Query: sqlite3 db "SELECT * FROM table;"                         │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 49 mein hum seekhenge:
- Proot-Distros in Termux
- Ubuntu, Debian, Kali Linux install
- Full Linux experience on Android
- Advanced system administration

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Thank you for watching! See you in Chapter 49!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. SQLite - Complete Guide

#### Installation

```bash
# Install SQLite
pkg install sqlite -y

# Verify installation
sqlite3 --version

# SQLite includes:
# - sqlite3 command-line tool
# - SQLite library
# - Documentation
```

#### SQLite Database Structure

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         SQLITE ARCHITECTURE                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    SQLite Database File (*.db)                   │   │
│   │                                                                   │   │
│   │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐            │   │
│   │   │   Table 1   │  │   Table 2   │  │   Index     │            │   │
│   │   │   (users)   │  │ (products)  │  │   (idx)     │            │   │
│   │   └─────────────┘  └─────────────┘  └─────────────┘            │   │
│   │                                                                   │   │
│   │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐            │   │
│   │   │   Trigger   │  │    View     │  │   Trigger   │            │   │
│   │   └─────────────┘  └─────────────┘  └─────────────┘            │   │
│   │                                                                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   Features:                                                              │
│   • Single file database                                                │
│   • No server required                                                  │
│   • Zero configuration                                                  │
│   • Cross-platform                                                      │
│   • ACID compliant                                                      │
│   • Supports up to 140TB                                                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### SQLite Data Types

| Type | Description | Example |
|------|-------------|---------|
| INTEGER | Signed integer | 1, 42, -100 |
| REAL | Floating point | 3.14, 2.5e10 |
| TEXT | UTF-8 string | 'Hello', "World" |
| BLOB | Binary data | Images, files |
| NULL | Null value | NULL |

#### SQLite Commands Reference

```sql
-- DATABASE COMMANDS

-- Create/Open database
.open mydb.db

-- Attach another database
ATTACH DATABASE 'other.db' AS other;

-- Detach database
DETACH DATABASE other;

-- Show databases
.databases

-- TABLE COMMANDS

-- Create table
CREATE TABLE users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT NOT NULL UNIQUE,
    email TEXT NOT NULL,
    password TEXT NOT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    is_active INTEGER DEFAULT 1
);

-- Create table with foreign key
CREATE TABLE orders (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_id INTEGER,
    product_name TEXT,
    quantity INTEGER,
    total_price REAL,
    order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

-- Show tables
.tables

-- Show table schema
.schema users
.schema

-- Rename table
ALTER TABLE users RENAME TO members;

-- Add column
ALTER TABLE users ADD COLUMN phone TEXT;

-- Drop table
DROP TABLE IF EXISTS users;

-- INDEX COMMANDS

-- Create index
CREATE INDEX idx_email ON users(email);
CREATE INDEX idx_username_email ON users(username, email);

-- Create unique index
CREATE UNIQUE INDEX idx_unique_email ON users(email);

-- Show indexes
.indexes

-- Drop index
DROP INDEX IF EXISTS idx_email;

-- CRUD OPERATIONS

-- INSERT
INSERT INTO users (username, email, password) VALUES ('rahul', 'rahul@email.com', 'pass123');
INSERT INTO users (username, email, password) VALUES 
    ('priya', 'priya@email.com', 'pass456'),
    ('amit', 'amit@email.com', 'pass789');

-- SELECT
SELECT * FROM users;
SELECT username, email FROM users;
SELECT * FROM users WHERE id = 1;
SELECT * FROM users WHERE is_active = 1 ORDER BY created_at DESC;
SELECT * FROM users WHERE email LIKE '%@gmail.com';
SELECT * FROM users LIMIT 10 OFFSET 5;

-- UPDATE
UPDATE users SET email = 'new@email.com' WHERE id = 1;
UPDATE users SET is_active = 0 WHERE created_at < '2024-01-01';

-- DELETE
DELETE FROM users WHERE id = 1;
DELETE FROM users WHERE is_active = 0;

-- AGGREGATE FUNCTIONS
SELECT COUNT(*) FROM users;
SELECT COUNT(*) as total FROM users WHERE is_active = 1;
SELECT AVG(age) FROM users;
SELECT SUM(total_price) FROM orders;
SELECT MAX(created_at) FROM orders;
SELECT MIN(created_at) FROM orders;

-- GROUP BY
SELECT is_active, COUNT(*) FROM users GROUP BY is_active;
SELECT user_id, COUNT(*) as order_count FROM orders GROUP BY user_id;

-- JOINS
SELECT users.username, orders.product_name 
FROM users 
INNER JOIN orders ON users.id = orders.user_id;

SELECT users.username, orders.product_name 
FROM users 
LEFT JOIN orders ON users.id = orders.user_id;

-- VIEWS
CREATE VIEW active_users AS 
SELECT username, email FROM users WHERE is_active = 1;

SELECT * FROM active_users;

DROP VIEW IF EXISTS active_users;

-- TRIGGERS
CREATE TRIGGER update_timestamp 
AFTER UPDATE ON users
BEGIN
    UPDATE users SET created_at = CURRENT_TIMESTAMP WHERE id = NEW.id;
END;

DROP TRIGGER IF EXISTS update_timestamp;

-- TRANSACTIONS
BEGIN TRANSACTION;
INSERT INTO users (username, email, password) VALUES ('test', 'test@email.com', 'test');
INSERT INTO orders (user_id, product_name, quantity) VALUES (last_insert_rowid(), 'Laptop', 1);
COMMIT;

-- Or rollback
ROLLBACK;

-- UTILITY COMMANDS

-- Enable foreign keys
PRAGMA foreign_keys = ON;

-- Check integrity
PRAGMA integrity_check;

-- Optimize database
VACUUM;

-- Analyze for query optimization
ANALYZE;

-- Export to SQL file
.output backup.sql
.dump
.output stdout

-- Import from SQL file
.read backup.sql

-- Format output
.mode column
.headers on
.width 10 20 30

-- CSV export
.mode csv
.output users.csv
SELECT * FROM users;
.output stdout

-- JSON output (SQLite 3.38+)
.mode json
SELECT * FROM users;
```

---

### 2. MySQL/MariaDB - Complete Guide

#### Installation

```bash
# Install MariaDB (MySQL compatible)
pkg install mariadb -y

# Initialize database
mysql_install_db

# Start server
mysqld_safe &

# Check if running
pgrep mysql

# Connect as root
mysql -u root

# Secure installation (optional script)
mysql_secure_installation
```

#### MySQL Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         MYSQL ARCHITECTURE                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    MySQL Server (mysqld)                         │   │
│   │                                                                   │   │
│   │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐            │   │
│   │   │ Connection  │  │   Query     │  │   Storage   │            │   │
│   │   │   Pool      │  │   Cache     │  │   Engines   │            │   │
│   │   └─────────────┘  └─────────────┘  └─────────────┘            │   │
│   │                                                                   │   │
│   │   ┌─────────────────────────────────────────────────────────┐   │   │
│   │   │              Storage Engines                              │   │   │
│   │   │  InnoDB  │  MyISAM  │  Memory  │  CSV  │  Archive       │   │   │
│   │   └─────────────────────────────────────────────────────────┘   │   │
│   │                                                                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   Port: 3306 (default)                                                  │
│   Data Directory: /data/data/com.termux/files/usr/var/lib/mysql         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### MySQL Data Types

| Category | Types | Description |
|----------|-------|-------------|
| Numeric | INT, BIGINT, SMALLINT, TINYINT, DECIMAL, FLOAT, DOUBLE | Numbers |
| String | CHAR, VARCHAR, TEXT, TINYTEXT, MEDIUMTEXT, LONGTEXT | Text data |
| Binary | BINARY, VARBINARY, BLOB, TINYBLOB, MEDIUMBLOB, LONGBLOB | Binary data |
| Date/Time | DATE, TIME, DATETIME, TIMESTAMP, YEAR | Temporal data |
| JSON | JSON | JSON documents |

#### MySQL Commands Reference

```sql
-- CONNECTION COMMANDS

-- Connect to MySQL
mysql -u root
mysql -u root -p
mysql -u user -p database_name
mysql -h hostname -u user -p

-- SERVER COMMANDS

-- Show status
SHOW STATUS;

-- Show variables
SHOW VARIABLES;
SHOW VARIABLES LIKE 'port';
SHOW VARIABLES LIKE 'char%';

-- Show processes
SHOW PROCESSLIST;

-- Kill process
KILL process_id;

-- DATABASE COMMANDS

-- Show databases
SHOW DATABASES;

-- Create database
CREATE DATABASE myapp;
CREATE DATABASE myapp CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Use database
USE myapp;

-- Show current database
SELECT DATABASE();

-- Drop database
DROP DATABASE IF EXISTS myapp;

-- Show database creation
SHOW CREATE DATABASE myapp;

-- TABLE COMMANDS

-- Create table
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    full_name VARCHAR(100),
    phone VARCHAR(20),
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- Create table with foreign key
CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    product_name VARCHAR(100) NOT NULL,
    quantity INT DEFAULT 1,
    unit_price DECIMAL(10,2),
    total_price DECIMAL(10,2),
    status ENUM('pending', 'processing', 'shipped', 'delivered', 'cancelled') DEFAULT 'pending',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);

-- Show tables
SHOW TABLES;

-- Describe table
DESCRIBE users;
DESC users;

-- Show table creation
SHOW CREATE TABLE users;

-- Alter table
ALTER TABLE users ADD COLUMN age INT;
ALTER TABLE users DROP COLUMN age;
ALTER TABLE users MODIFY COLUMN email VARCHAR(200);
ALTER TABLE users CHANGE COLUMN full_name name VARCHAR(100);
ALTER TABLE users ADD INDEX idx_email (email);
ALTER TABLE users DROP INDEX idx_email;

-- Truncate table (delete all data)
TRUNCATE TABLE users;

-- Drop table
DROP TABLE IF EXISTS users;

-- CRUD OPERATIONS

-- INSERT
INSERT INTO users (username, email, password, full_name) 
VALUES ('rahul', 'rahul@email.com', MD5('password123'), 'Rahul Kumar');

INSERT INTO users (username, email, password) VALUES 
    ('priya', 'priya@email.com', MD5('pass456')),
    ('amit', 'amit@email.com', MD5('pass789')),
    ('neha', 'neha@email.com', MD5('pass111'));

-- SELECT
SELECT * FROM users;
SELECT id, username, email FROM users;
SELECT * FROM users WHERE id = 1;
SELECT * FROM users WHERE is_active = TRUE;
SELECT * FROM users WHERE created_at > '2024-01-01';
SELECT * FROM users WHERE email LIKE '%@gmail.com';
SELECT * FROM users WHERE username IN ('rahul', 'priya');
SELECT * FROM users ORDER BY created_at DESC LIMIT 10;
SELECT * FROM users LIMIT 5 OFFSET 10;

-- UPDATE
UPDATE users SET email = 'new@email.com' WHERE id = 1;
UPDATE users SET is_active = FALSE, updated_at = NOW() WHERE id = 2;

-- DELETE
DELETE FROM users WHERE id = 1;
DELETE FROM users WHERE is_active = FALSE;

-- JOINS

-- Inner join
SELECT users.username, orders.product_name, orders.total_price
FROM users
INNER JOIN orders ON users.id = orders.user_id;

-- Left join
SELECT users.username, COUNT(orders.id) as order_count
FROM users
LEFT JOIN orders ON users.id = orders.user_id
GROUP BY users.id;

-- Multiple joins
SELECT u.username, o.product_name, p.payment_method
FROM users u
JOIN orders o ON u.id = o.user_id
LEFT JOIN payments p ON o.id = p.order_id;

-- AGGREGATE FUNCTIONS
SELECT COUNT(*) as total_users FROM users;
SELECT COUNT(DISTINCT user_id) as unique_customers FROM orders;
SELECT SUM(total_price) as total_revenue FROM orders;
SELECT AVG(total_price) as average_order FROM orders;
SELECT MAX(created_at) as latest_order FROM orders;
SELECT MIN(created_at) as first_order FROM orders;

-- GROUP BY & HAVING
SELECT user_id, COUNT(*) as order_count, SUM(total_price) as total_spent
FROM orders
GROUP BY user_id
HAVING total_spent > 1000
ORDER BY total_spent DESC;

-- USER MANAGEMENT

-- Create user
CREATE USER 'appuser'@'localhost' IDENTIFIED BY 'securepassword';
CREATE USER 'admin'@'%' IDENTIFIED BY 'adminpassword';

-- Grant privileges
GRANT ALL PRIVILEGES ON myapp.* TO 'appuser'@'localhost';
GRANT SELECT, INSERT, UPDATE ON myapp.* TO 'readonly'@'localhost';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' WITH GRANT OPTION;

-- Show grants
SHOW GRANTS FOR 'appuser'@'localhost';

-- Revoke privileges
REVOKE INSERT, UPDATE ON myapp.* FROM 'appuser'@'localhost';

-- Drop user
DROP USER 'appuser'@'localhost';

-- Flush privileges
FLUSH PRIVILEGES;

-- BACKUP & RESTORE

-- Backup database
-- mysqldump -u root database_name > backup.sql
-- mysqldump -u root --all-databases > all_backup.sql
-- mysqldump -u root database_name table_name > table_backup.sql

-- Restore database
-- mysql -u root database_name < backup.sql

-- INDEXES

-- Create index
CREATE INDEX idx_username ON users(username);
CREATE INDEX idx_created ON orders(created_at);
CREATE UNIQUE INDEX idx_unique_email ON users(email);
CREATE FULLTEXT INDEX idx_fulltext_content ON posts(content);

-- Show indexes
SHOW INDEX FROM users;

-- Drop index
DROP INDEX idx_username ON users;

-- VIEWS

-- Create view
CREATE VIEW active_users AS
SELECT id, username, email FROM users WHERE is_active = TRUE;

-- Create or replace view
CREATE OR REPLACE VIEW user_orders AS
SELECT u.id, u.username, COUNT(o.id) as order_count
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
GROUP BY u.id;

-- Show views
SHOW FULL TABLES WHERE Table_type = 'VIEW';

-- Drop view
DROP VIEW IF EXISTS active_users;

-- STORED PROCEDURES

-- Create procedure
DELIMITER //
CREATE PROCEDURE GetUserOrders(IN user_id INT)
BEGIN
    SELECT * FROM orders WHERE orders.user_id = user_id;
END //
DELIMITER ;

-- Call procedure
CALL GetUserOrders(1);

-- Drop procedure
DROP PROCEDURE IF EXISTS GetUserOrders;

-- FUNCTIONS

DELIMITER //
CREATE FUNCTION CalculateTotal(quantity INT, price DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN quantity * price;
END //
DELIMITER ;

-- Use function
SELECT CalculateTotal(5, 100.00);

-- TRIGGERS

DELIMITER //
CREATE TRIGGER before_user_insert
BEFORE INSERT ON users
FOR EACH ROW
BEGIN
    SET NEW.created_at = NOW();
END //
DELIMITER ;

DROP TRIGGER IF EXISTS before_user_insert;
```

#### MySQL Configuration Files

```bash
# Location in Termux
$PREFIX/etc/my.cnf
$PREFIX/etc/my.cnf.d/

# Basic configuration
[mysqld]
port = 3306
socket = /tmp/mysql.sock
datadir = /data/data/com.termux/files/usr/var/lib/mysql
bind-address = 127.0.0.1

# Performance settings
innodb_buffer_pool_size = 128M
max_connections = 100
query_cache_size = 16M

# Logging
log_error = /tmp/mysql_error.log
slow_query_log = 1
slow_query_log_file = /tmp/mysql_slow.log
```

---

### 3. PostgreSQL - Complete Guide

#### Installation

```bash
# Install PostgreSQL
pkg install postgresql -y

# Create data directory
mkdir -p ~/postgres-data

# Initialize database cluster
initdb ~/postgres-data

# Start server
pg_ctl -D ~/postgres-data -l ~/postgres-log start

# Connect to database
psql

# Stop server
pg_ctl -D ~/postgres-data stop

# Restart server
pg_ctl -D ~/postgres-data restart

# Check status
pg_ctl -D ~/postgres-data status
```

#### PostgreSQL Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                       POSTGRESQL ARCHITECTURE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                  PostgreSQL Server (postgres)                     │   │
│   │                                                                   │   │
│   │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐            │   │
│   │   │ Postmaster  │  │  Background │  │   WAL       │            │   │
│   │   │  Process    │  │   Writer    │  │  Archiver   │            │   │
│   │   └─────────────┘  └─────────────┘  └─────────────┘            │   │
│   │                                                                   │   │
│   │   ┌─────────────────────────────────────────────────────────┐   │   │
│   │   │              Data Directory                              │   │   │
│   │   │  base/  │  global/  │  pg_wal/  │  pg_log/             │   │   │
│   │   └─────────────────────────────────────────────────────────┘   │   │
│   │                                                                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   Port: 5432 (default)                                                  │
│   Features: ACID, MVCC, JSONB, Full-text search, GIS                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### PostgreSQL Commands Reference

```sql
-- CONNECTION COMMANDS

-- Connect to database
psql
psql -d database_name
psql -U username -d database_name
psql -h hostname -p port -U username -d database_name

-- META-COMMANDS (inside psql)

\l              -- List databases
\c dbname       -- Connect to database
\dt             -- List tables
\d tablename    -- Describe table
\du             -- List users/roles
\df             -- List functions
\di             -- List indexes
\dv             -- List views
\dn             -- List schemas
\dp             -- List privileges
\conninfo       -- Show connection info
\q              -- Quit

-- DATABASE COMMANDS

-- Create database
CREATE DATABASE myapp;
CREATE DATABASE myapp WITH ENCODING 'UTF8';

-- Drop database
DROP DATABASE IF EXISTS myapp;

-- TABLE COMMANDS

-- Create table
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    metadata JSONB DEFAULT '{}',
    created_at TIMESTAMP DEFAULT NOW()
);

-- Create table with auto-increment
CREATE TABLE products (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(10,2),
    tags TEXT[],
    created_at TIMESTAMP DEFAULT NOW()
);

-- Advanced types
CREATE TABLE events (
    id SERIAL PRIMARY KEY,
    event_name VARCHAR(100),
    event_data JSONB,
    location POINT,
    event_time TIMESTAMPTZ DEFAULT NOW()
);

-- CRUD OPERATIONS

-- INSERT
INSERT INTO users (username, email, password) 
VALUES ('rahul', 'rahul@email.com', 'hashed_password');

INSERT INTO users (username, email, password, metadata) VALUES 
    ('priya', 'priya@email.com', 'hash', '{"age": 25, "city": "Delhi"}'),
    ('amit', 'amit@email.com', 'hash', '{"age": 30, "city": "Mumbai"}');

-- JSONB operations
INSERT INTO events (event_name, event_data, location) VALUES 
    ('login', '{"user": "rahul", "ip": "192.168.1.1"}', POINT(28.6, 77.2));

-- SELECT
SELECT * FROM users;
SELECT username, email FROM users WHERE id = 1;
SELECT * FROM users WHERE metadata->>'city' = 'Delhi';
SELECT * FROM events WHERE event_data @> '{"user": "rahul"}';

-- Array operations
SELECT * FROM products WHERE tags @> ARRAY['electronics'];
SELECT array_length(tags, 1) FROM products;

-- UPDATE
UPDATE users SET email = 'new@email.com' WHERE id = 1;
UPDATE users SET metadata = metadata || '{"phone": "123456"}' WHERE id = 1;

-- DELETE
DELETE FROM users WHERE id = 1;

-- JSONB QUERIES

-- Get JSON value
SELECT event_data->>'user' FROM events;
SELECT event_data->'user' FROM events;

-- Check if key exists
SELECT * FROM events WHERE event_data ? 'user';

-- Contains query
SELECT * FROM events WHERE event_data @> '{"user": "rahul"}';

-- USER MANAGEMENT

-- Create user
CREATE USER appuser WITH PASSWORD 'securepassword';

-- Create role with attributes
CREATE ROLE admin WITH LOGIN PASSWORD 'adminpass' SUPERUSER CREATEDB;

-- Grant privileges
GRANT ALL PRIVILEGES ON DATABASE myapp TO appuser;
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO appuser;
GRANT USAGE, SELECT ON ALL SEQUENCES IN SCHEMA public TO appuser;

-- ALTER user
ALTER USER appuser WITH PASSWORD 'newpassword';

-- Drop user
DROP USER appuser;

-- BACKUP & RESTORE

-- Backup database
-- pg_dump myapp > myapp_backup.sql
-- pg_dump -U username -d myapp > backup.sql
-- pg_dumpall > all_databases.sql

-- Restore database
-- psql myapp < myapp_backup.sql

-- INDEXES

-- Create index
CREATE INDEX idx_email ON users(email);
CREATE INDEX idx_metadata ON users USING GIN(metadata);
CREATE INDEX idx_location ON events USING GIST(location);

-- Full-text search
CREATE INDEX idx_search ON products USING GIN(to_tsvector('english', name));

-- FUNCTIONS

CREATE OR REPLACE FUNCTION get_user_count()
RETURNS INTEGER AS $$
BEGIN
    RETURN (SELECT COUNT(*) FROM users);
END;
$$ LANGUAGE plpgsql;

-- Call function
SELECT get_user_count();

-- VIEWS

CREATE VIEW active_users AS
SELECT id, username, email FROM users WHERE created_at > NOW() - INTERVAL '30 days';

SELECT * FROM active_users;
```

---

### 4. Redis - Complete Guide

#### Installation

```bash
# Install Redis
pkg install redis -y

# Start server (foreground)
redis-server

# Start server (background)
redis-server --daemonize yes

# Start with config file
redis-server /path/to/redis.conf

# Connect client
redis-cli
redis-cli -h 127.0.0.1 -p 6379
redis-cli -a password

# Check server info
redis-cli INFO

# Ping server
redis-cli PING

# Stop server
redis-cli shutdown
```

#### Redis Data Types

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         REDIS DATA TYPES                                 │
├────────────────┬────────────────────────────────────────────────────────┤
│ Type           │ Description & Commands                                  │
├────────────────┼────────────────────────────────────────────────────────┤
│ String         │ SET, GET, INCR, DECR, APPEND                           │
│ Hash           │ HSET, HGET, HGETALL, HMSET, HDEL                       │
│ List           │ LPUSH, RPUSH, LPOP, RPOP, LRANGE, LLEN                 │
│ Set            │ SADD, SREM, SMEMBERS, SISMEMBER, SCARD                 │
│ Sorted Set     │ ZADD, ZREM, ZRANGE, ZSCORE, ZRANK                      │
│ Bitmap         │ SETBIT, GETBIT, BITCOUNT                                │
│ HyperLogLog    │ PFADD, PFCOUNT, PFMERGE                                │
│ Stream         │ XADD, XREAD, XRANGE, XLEN                              │
│ JSON           │ JSON.SET, JSON.GET (with RedisJSON module)             │
└────────────────┴────────────────────────────────────────────────────────┘
```

#### Redis Commands Reference

```bash
# STRINGS

SET key value
SET mykey "Hello Termux"
SET counter 100
SETNX mykey "value"           # Set if not exists
SETEX mykey 60 "value"        # Set with expiry (60 seconds)
GET mykey                     # Returns "Hello Termux"
GETRANGE mykey 0 4            # Returns "Hello"
STRLEN mykey                  # Returns length
INCR counter                  # Increment by 1
INCRBY counter 10             # Increment by 10
DECR counter                  # Decrement by 1
APPEND mykey " World"         # Appends to value
MSET k1 "v1" k2 "v2"          # Set multiple
MGET k1 k2                    # Get multiple
DEL mykey                     # Delete key
EXISTS mykey                  # Check existence (1=exists, 0=not)
EXPIRE mykey 10               # Set expiry (10 seconds)
TTL mykey                     # Time to live (-1=no expiry, -2=expired)
TYPE mykey                    # Show type

# HASHES (for objects)

HSET user:1 name "Rahul"
HSET user:1 email "rahul@email.com"
HSET user:1 age 25
HGET user:1 name              # Returns "Rahul"
HGETALL user:1                # Returns all fields
HMSET user:2 name "Priya" email "priya@email.com" age 22
HMGET user:1 name email       # Get multiple fields
HEXISTS user:1 name           # Check field exists
HDEL user:1 age               # Delete field
HKEYS user:1                  # Get all keys
HVALS user:1                  # Get all values
HLEN user:1                   # Number of fields
HINCRBY user:1 age 1          # Increment field

# LISTS (ordered collections)

LPUSH mylist "first"          # Add to left
RPUSH mylist "last"           # Add to right
LPUSH mylist "second" "third" # Add multiple
LPOP mylist                   # Remove from left
RPOP mylist                   # Remove from right
LRANGE mylist 0 -1            # Get all elements
LLEN mylist                   # Length
LINDEX mylist 0               # Get element at index
LSET mylist 0 "new_value"     # Set at index
LREM mylist 1 "value"         # Remove occurrences

# SETS (unordered unique elements)

SADD myset "one"
SADD myset "two" "three"
SMEMBERS myset                # Get all members
SISMEMBER myset "one"         # Check membership
SCARD myset                   # Count members
SREM myset "one"              # Remove member
SPOP myset                    # Pop random member
SRANDMEMBER myset             # Get random member

# Set operations
SADD set1 "a" "b" "c"
SADD set2 "b" "c" "d"
SINTER set1 set2              # Intersection
SUNION set1 set2              # Union
SDIFF set1 set2               # Difference

# SORTED SETS (with scores)

ZADD leaderboard 100 "player1"
ZADD leaderboard 200 "player2" 150 "player3"
ZRANGE leaderboard 0 -1       # Range by rank
ZRANGE leaderboard 0 -1 WITHSCORES
ZREVRANGE leaderboard 0 -1 WITHSCORES  # Descending
ZSCORE leaderboard "player1"  # Get score
ZRANK leaderboard "player1"   # Get rank
ZINCRBY leaderboard 50 "player1"  # Increment score
ZREM leaderboard "player1"    # Remove member
ZCARD leaderboard             # Count members

# KEYS & SERVER

KEYS *                        # List all keys
KEYS user:*                   # Pattern match
SCAN 0 MATCH user:* COUNT 10  # Iterate keys
TYPE keyname                  # Get key type
RENAME oldkey newkey          # Rename key
DUMP keyname                  # Serialize value
RESTORE keyname 0 serialized  # Restore from dump
FLUSHDB                       # Clear current database
FLUSHALL                      # Clear all databases
SELECT 1                      # Switch to database 1
DBSIZE                        # Count keys in current DB
INFO                          # Server info
CONFIG GET maxmemory          # Get config
CONFIG SET maxmemory 256mb    # Set config
SAVE                          # Save to disk
BGSAVE                        # Background save
LASTSAVE                      # Last save time
CLIENT LIST                   # Connected clients
TIME                          # Server time
```

---

### 5. MongoDB - Complete Guide

#### Installation in Termux

```bash
# MongoDB is not directly available in main Termux repo
# Option 1: Use mongosh with remote MongoDB
pkg install mongosh -y

# Option 2: Install via proot-distro
pkg install proot-distro -y
proot-distro install ubuntu
proot-distro login ubuntu
# Then inside Ubuntu:
apt update
apt install mongodb

# Option 3: Use Docker-style container
# For development, use MongoDB Atlas (free tier)
```

#### MongoDB Commands Reference

```javascript
// CONNECTION
mongosh "mongodb://localhost:27017"
mongosh "mongodb+srv://cluster.mongodb.net/mydb" --username myuser

// DATABASE OPERATIONS
show dbs                    // List databases
use myapp                   // Switch/create database
db                          // Current database
db.dropDatabase()           // Drop database

// COLLECTION OPERATIONS
show collections            // List collections
db.createCollection("users")    // Create collection
db.users.drop()             // Drop collection

// CRUD OPERATIONS

// INSERT
db.users.insertOne({
    name: "Rahul",
    email: "rahul@email.com",
    age: 25,
    skills: ["Python", "JavaScript"],
    address: {
        city: "Delhi",
        country: "India"
    }
})

db.users.insertMany([
    { name: "Priya", email: "priya@email.com", age: 22 },
    { name: "Amit", email: "amit@email.com", age: 28 }
])

// FIND
db.users.find()                             // All documents
db.users.find({ name: "Rahul" })            // Filter
db.users.find({ age: { $gt: 25 } })         // Greater than
db.users.find({ age: { $gte: 25 } })        // Greater than or equal
db.users.find({ age: { $lt: 30 } })         // Less than
db.users.find({ skills: "Python" })         // Array contains
db.users.find({ "address.city": "Delhi" })  // Nested field
db.users.findOne()                          // Single document
db.users.find().pretty()                    // Formatted output
db.users.find().limit(5)                    // Limit results
db.users.find().skip(5)                     // Skip results
db.users.find().sort({ age: -1 })           // Sort descending
db.users.find({}, { name: 1, email: 1, _id: 0 })  // Projection

// UPDATE
db.users.updateOne(
    { name: "Rahul" },
    { $set: { age: 26, city: "Mumbai" } }
)

db.users.updateMany(
    { age: { $lt: 25 } },
    { $set: { status: "young" } }
)

db.users.updateOne(
    { name: "Rahul" },
    { $push: { skills: "MongoDB" } }        // Add to array
)

db.users.updateOne(
    { name: "Rahul" },
    { $inc: { age: 1 } }                    // Increment
)

db.users.updateOne(
    { name: "Rahul" },
    { $unset: { city: "" } }                // Remove field
)

// DELETE
db.users.deleteOne({ name: "Rahul" })
db.users.deleteMany({ age: { $lt: 20 } })
db.users.deleteMany({})                    // Delete all

// AGGREGATION
db.users.aggregate([
    { $match: { age: { $gte: 20 } } },
    { $group: { _id: "$city", count: { $sum: 1 } } },
    { $sort: { count: -1 } }
])

// INDEXES
db.users.createIndex({ email: 1 })
db.users.createIndex({ name: 1, age: -1 })
db.users.getIndexes()
db.users.dropIndex("email_1")

// USER MANAGEMENT
db.createUser({
    user: "appuser",
    pwd: "password123",
    roles: [{ role: "readWrite", db: "myapp" }]
})

db.dropUser("appuser")
db.getUsers()
```

---

### 6. Database Connectivity with Python

#### SQLite with Python

```python
#!/usr/bin/env python3
"""SQLite Database Demo in Termux"""

import sqlite3
import os

class SQLiteDatabase:
    def __init__(self, db_name='app.db'):
        self.db_name = db_name
        self.conn = None
        self.cursor = None
    
    def connect(self):
        """Connect to SQLite database"""
        self.conn = sqlite3.connect(self.db_name)
        self.cursor = self.conn.cursor()
        print(f"[+] Connected to {self.db_name}")
    
    def create_table(self):
        """Create users table"""
        self.cursor.execute('''
            CREATE TABLE IF NOT EXISTS users (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                name TEXT NOT NULL,
                email TEXT UNIQUE,
                age INTEGER,
                created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
            )
        ''')
        self.conn.commit()
        print("[+] Table created successfully")
    
    def insert_user(self, name, email, age):
        """Insert a user"""
        try:
            self.cursor.execute(
                "INSERT INTO users (name, email, age) VALUES (?, ?, ?)",
                (name, email, age)
            )
            self.conn.commit()
            print(f"[+] Inserted: {name}")
        except sqlite3.IntegrityError:
            print(f"[-] Email already exists: {email}")
    
    def get_users(self):
        """Get all users"""
        self.cursor.execute("SELECT * FROM users")
        return self.cursor.fetchall()
    
    def get_user_by_id(self, user_id):
        """Get user by ID"""
        self.cursor.execute("SELECT * FROM users WHERE id = ?", (user_id,))
        return self.cursor.fetchone()
    
    def update_user(self, user_id, name=None, email=None, age=None):
        """Update user"""
        updates = []
        values = []
        if name:
            updates.append("name = ?")
            values.append(name)
        if email:
            updates.append("email = ?")
            values.append(email)
        if age is not None:
            updates.append("age = ?")
            values.append(age)
        
        values.append(user_id)
        query = f"UPDATE users SET {', '.join(updates)} WHERE id = ?"
        self.cursor.execute(query, values)
        self.conn.commit()
        print(f"[+] Updated user ID: {user_id}")
    
    def delete_user(self, user_id):
        """Delete user"""
        self.cursor.execute("DELETE FROM users WHERE id = ?", (user_id,))
        self.conn.commit()
        print(f"[+] Deleted user ID: {user_id}")
    
    def close(self):
        """Close connection"""
        if self.conn:
            self.conn.close()
            print("[+] Connection closed")

# Usage
if __name__ == "__main__":
    db = SQLiteDatabase('myapp.db')
    db.connect()
    db.create_table()
    
    # Insert users
    db.insert_user("Rahul", "rahul@email.com", 25)
    db.insert_user("Priya", "priya@email.com", 22)
    db.insert_user("Amit", "amit@email.com", 28)
    
    # Get all users
    print("\nAll Users:")
    for user in db.get_users():
        print(user)
    
    # Update user
    db.update_user(1, age=26)
    
    # Delete user
    db.delete_user(3)
    
    db.close()
```

#### MySQL with Python

```python
#!/usr/bin/env python3
"""MySQL Database Demo in Termux"""

# Install: pip install mysql-connector-python

import mysql.connector
from mysql.connector import Error

class MySQLDatabase:
    def __init__(self, host='localhost', user='root', password='', database='myapp'):
        self.host = host
        self.user = user
        self.password = password
        self.database = database
        self.conn = None
        self.cursor = None
    
    def connect(self):
        """Connect to MySQL database"""
        try:
            self.conn = mysql.connector.connect(
                host=self.host,
                user=self.user,
                password=self.password,
                database=self.database
            )
            self.cursor = self.conn.cursor(dictionary=True)
            print(f"[+] Connected to MySQL database: {self.database}")
        except Error as e:
            print(f"[-] Connection error: {e}")
    
    def create_table(self):
        """Create products table"""
        self.cursor.execute('''
            CREATE TABLE IF NOT EXISTS products (
                id INT AUTO_INCREMENT PRIMARY KEY,
                name VARCHAR(100) NOT NULL,
                price DECIMAL(10,2),
                stock INT DEFAULT 0,
                created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
            )
        ''')
        self.conn.commit()
        print("[+] Table created successfully")
    
    def insert_product(self, name, price, stock):
        """Insert a product"""
        self.cursor.execute(
            "INSERT INTO products (name, price, stock) VALUES (%s, %s, %s)",
            (name, price, stock)
        )
        self.conn.commit()
        print(f"[+] Inserted: {name}")
    
    def get_products(self):
        """Get all products"""
        self.cursor.execute("SELECT * FROM products")
        return self.cursor.fetchall()
    
    def search_products(self, keyword):
        """Search products by name"""
        self.cursor.execute(
            "SELECT * FROM products WHERE name LIKE %s",
            (f"%{keyword}%",)
        )
        return self.cursor.fetchall()
    
    def close(self):
        """Close connection"""
        if self.conn and self.conn.is_connected():
            self.cursor.close()
            self.conn.close()
            print("[+] Connection closed")

# Usage
if __name__ == "__main__":
    db = MySQLDatabase(user='root', database='myapp')
    db.connect()
    db.create_table()
    
    db.insert_product("Laptop", 50000.00, 10)
    db.insert_product("Mouse", 500.00, 50)
    db.insert_product("Keyboard", 1500.00, 30)
    
    print("\nAll Products:")
    for product in db.get_products():
        print(product)
    
    db.close()
```

#### Redis with Python

```python
#!/usr/bin/env python3
"""Redis Demo in Termux"""

# Install: pip install redis

import redis
import json

class RedisClient:
    def __init__(self, host='localhost', port=6379, db=0):
        self.client = redis.Redis(host=host, port=port, db=db, decode_responses=True)
    
    def set_string(self, key, value, expire=None):
        """Set string value"""
        if expire:
            self.client.setex(key, expire, value)
        else:
            self.client.set(key, value)
        print(f"[+] Set: {key} = {value}")
    
    def get_string(self, key):
        """Get string value"""
        return self.client.get(key)
    
    def set_hash(self, name, data):
        """Set hash (object)"""
        self.client.hset(name, mapping=data)
        print(f"[+] Set hash: {name}")
    
    def get_hash(self, name):
        """Get all hash fields"""
        return self.client.hgetall(name)
    
    def push_list(self, key, *values):
        """Push to list"""
        self.client.rpush(key, *values)
        print(f"[+] Pushed to list: {key}")
    
    def get_list(self, key):
        """Get list items"""
        return self.client.lrange(key, 0, -1)
    
    def add_set(self, key, *values):
        """Add to set"""
        self.client.sadd(key, *values)
        print(f"[+] Added to set: {key}")
    
    def get_set(self, key):
        """Get set members"""
        return self.client.smembers(key)
    
    def cache_json(self, key, data, expire=300):
        """Cache JSON data"""
        self.client.setex(key, expire, json.dumps(data))
        print(f"[+] Cached JSON: {key}")
    
    def get_cached_json(self, key):
        """Get cached JSON"""
        data = self.client.get(key)
        return json.loads(data) if data else None
    
    def delete(self, *keys):
        """Delete keys"""
        self.client.delete(*keys)
        print(f"[+] Deleted keys: {keys}")

# Usage
if __name__ == "__main__":
    r = RedisClient()
    
    # Strings
    r.set_string("app_name", "Termux Demo")
    r.set_string("session:123", "user_data", expire=60)
    print(r.get_string("app_name"))
    
    # Hashes
    r.set_hash("user:1", {"name": "Rahul", "email": "rahul@email.com"})
    print(r.get_hash("user:1"))
    
    # Lists
    r.push_list("tasks", "Task 1", "Task 2", "Task 3")
    print(r.get_list("tasks"))
    
    # Sets
    r.add_set("tags", "python", "termux", "database")
    print(r.get_set("tags"))
    
    # JSON Cache
    r.cache_json("api:response", {"status": "ok", "data": [1, 2, 3]})
    print(r.get_cached_json("api:response"))
```

---

### 7. PHP + MySQL Integration

```php
<?php
// database.php - PHP MySQL Connection in Termux

// Install PHP: pkg install php
// Install MySQL: pkg install mariadb
// Start MySQL: mysqld_safe &

class Database {
    private $host = 'localhost';
    private $user = 'root';
    private $password = '';
    private $database = 'myapp';
    private $conn;
    
    public function __construct() {
        $this->connect();
    }
    
    private function connect() {
        $this->conn = new mysqli(
            $this->host,
            $this->user,
            $this->password,
            $this->database
        );
        
        if ($this->conn->connect_error) {
            die("Connection failed: " . $this->conn->connect_error);
        }
        
        echo "[+] Connected to MySQL\n";
    }
    
    public function createTable() {
        $sql = "CREATE TABLE IF NOT EXISTS users (
            id INT AUTO_INCREMENT PRIMARY KEY,
            name VARCHAR(100) NOT NULL,
            email VARCHAR(100) UNIQUE,
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        )";
        
        if ($this->conn->query($sql) === TRUE) {
            echo "[+] Table created\n";
        }
    }
    
    public function insertUser($name, $email) {
        $stmt = $this->conn->prepare("INSERT INTO users (name, email) VALUES (?, ?)");
        $stmt->bind_param("ss", $name, $email);
        
        if ($stmt->execute()) {
            echo "[+] User inserted: $name\n";
        }
        $stmt->close();
    }
    
    public function getUsers() {
        $result = $this->conn->query("SELECT * FROM users");
        $users = [];
        
        while ($row = $result->fetch_assoc()) {
            $users[] = $row;
        }
        
        return $users;
    }
    
    public function getUserById($id) {
        $stmt = $this->conn->prepare("SELECT * FROM users WHERE id = ?");
        $stmt->bind_param("i", $id);
        $stmt->execute();
        
        return $stmt->get_result()->fetch_assoc();
    }
    
    public function updateUser($id, $name, $email) {
        $stmt = $this->conn->prepare("UPDATE users SET name = ?, email = ? WHERE id = ?");
        $stmt->bind_param("ssi", $name, $email, $id);
        
        if ($stmt->execute()) {
            echo "[+] User updated\n";
        }
        $stmt->close();
    }
    
    public function deleteUser($id) {
        $stmt = $this->conn->prepare("DELETE FROM users WHERE id = ?");
        $stmt->bind_param("i", $id);
        
        if ($stmt->execute()) {
            echo "[+] User deleted\n";
        }
        $stmt->close();
    }
    
    public function close() {
        $this->conn->close();
        echo "[+] Connection closed\n";
    }
}

// Usage
$db = new Database();
$db->createTable();

$db->insertUser("Rahul", "rahul@email.com");
$db->insertUser("Priya", "priya@email.com");

echo "\nAll Users:\n";
foreach ($db->getUsers() as $user) {
    echo "ID: {$user['id']}, Name: {$user['name']}, Email: {$user['email']}\n";
}

$db->close();
?>
```

Run PHP file:
```bash
php database.php
```

---

### 8. Database Security Best Practices

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    DATABASE SECURITY CHECKLIST                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  AUTHENTICATION                                                          │
│  ☐ Use strong passwords (12+ chars, mixed)                             │
│  ☐ Change default passwords immediately                                 │
│  ☐ Remove anonymous users                                               │
│  ☐ Disable root remote login                                            │
│  ☐ Use separate users for applications                                  │
│                                                                          │
│  AUTHORIZATION                                                           │
│  ☐ Grant minimum required privileges                                    │
│  ☐ Use separate database users per application                          │
│  ☐ Revoke unnecessary privileges                                        │
│  ☐ Regularly audit user permissions                                     │
│                                                                          │
│  NETWORK SECURITY                                                        │
│  ☐ Bind to localhost only (no external access)                         │
│  ☐ Use firewall rules                                                   │
│  ☐ Enable SSL/TLS for connections                                       │
│  ☐ Disable remote root access                                           │
│                                                                          │
│  DATA PROTECTION                                                         │
│  ☐ Encrypt sensitive data                                               │
│  ☐ Hash passwords (bcrypt, argon2)                                      │
│  ☐ Use prepared statements (prevent SQL injection)                      │
│  ☐ Validate and sanitize input                                          │
│                                                                          │
│  BACKUP & RECOVERY                                                       │
│  ☐ Regular automated backups                                            │
│  ☐ Test restore procedures                                              │
│  ☐ Store backups securely (encrypted)                                   │
│  ☐ Multiple backup locations                                            │
│                                                                          │
│  MONITORING                                                              │
│  ☐ Enable query logging                                                 │
│  ☐ Monitor for suspicious activity                                      │
│  ☐ Set up alerts for anomalies                                          │
│  ☐ Regular security audits                                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### SQL Injection Prevention

```python
# BAD - Vulnerable to SQL Injection
def get_user_bad(username):
    query = f"SELECT * FROM users WHERE username = '{username}'"
    cursor.execute(query)  # Dangerous!

# Attack: username = "' OR '1'='1"
# Result: SELECT * FROM users WHERE username = '' OR '1'='1'

# GOOD - Using parameterized queries
def get_user_good(username):
    query = "SELECT * FROM users WHERE username = ?"
    cursor.execute(query, (username,))  # Safe!
```

---

## 📋 COMMANDS REFERENCE

### SQLite Commands

```bash
# Installation
pkg install sqlite -y

# Start SQLite with database
sqlite3 mydb.db

# Execute SQL from command line
sqlite3 mydb.db "SELECT * FROM users;"

# Import CSV
sqlite3 mydb.db ".import --csv data.csv tablename"

# Export to CSV
sqlite3 mydb.db ".mode csv" ".output data.csv" "SELECT * FROM users;"

# Backup
sqlite3 mydb.db ".backup 'backup.db'"

# Check integrity
sqlite3 mydb.db "PRAGMA integrity_check;"

# Get database info
sqlite3 mydb.db ".databases"
sqlite3 mydb.db ".tables"
sqlite3 mydb.db ".schema"
```

### MySQL/MariaDB Commands

```bash
# Installation
pkg install mariadb -y
mysql_install_db

# Start server
mysqld_safe &

# Connect as root
mysql -u root

# Connect with password
mysql -u root -p

# Connect to specific database
mysql -u user -p database_name

# Backup database
mysqldump -u root database_name > backup.sql

# Backup all databases
mysqldump -u root --all-databases > all_backup.sql

# Restore database
mysql -u root database_name < backup.sql

# Check server status
mysqladmin -u root status

# Stop server
mysqladmin -u root shutdown

# Kill MySQL processes
pkill mysqld
```

### PostgreSQL Commands

```bash
# Installation
pkg install postgresql -y

# Initialize
initdb ~/postgres-data

# Start server
pg_ctl -D ~/postgres-data -l ~/postgres.log start

# Stop server
pg_ctl -D ~/postgres-data stop

# Restart server
pg_ctl -D ~/postgres-data restart

# Connect
psql
psql -d database_name

# Backup
pg_dump database_name > backup.sql
pg_dumpall > all_databases.sql

# Restore
psql database_name < backup.sql

# Check status
pg_ctl -D ~/postgres-data status
```

### Redis Commands

```bash
# Installation
pkg install redis -y

# Start server (foreground)
redis-server

# Start server (background)
redis-server --daemonize yes

# Connect client
redis-cli

# Execute command
redis-cli PING
redis-cli SET key value
redis-cli GET key

# Check info
redis-cli INFO

# Monitor commands
redis-cli MONITOR

# Stop server
redis-cli shutdown

# Flush database
redis-cli FLUSHDB
redis-cli FLUSHALL
```

### Python Database Libraries

```bash
# SQLite (built-in with Python)
pkg install python -y

# MySQL connector
pip install mysql-connector-python

# PostgreSQL adapter
pip install psycopg2-binary

# Redis client
pip install redis

# MongoDB driver
pip install pymongo

# SQLAlchemy (ORM)
pip install sqlalchemy

# Peewee (lightweight ORM)
pip install peewee
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: SQLite Database Creation

```bash
# Task: Create a complete SQLite database for a todo app

# Step 1: Create database
sqlite3 todo_app.db

# Step 2: Create tables
CREATE TABLE categories (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL UNIQUE
);

CREATE TABLE todos (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    title TEXT NOT NULL,
    description TEXT,
    category_id INTEGER,
    priority INTEGER DEFAULT 1,
    completed INTEGER DEFAULT 0,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (category_id) REFERENCES categories(id)
);

# Step 3: Insert categories
INSERT INTO categories (name) VALUES ('Work');
INSERT INTO categories (name) VALUES ('Personal');
INSERT INTO categories (name) VALUES ('Shopping');

# Step 4: Insert todos
INSERT INTO todos (title, category_id, priority) VALUES ('Complete project', 1, 3);
INSERT INTO todos (title, category_id, priority) VALUES ('Buy groceries', 3, 2);
INSERT INTO todos (title, description, category_id) VALUES ('Exercise', '30 min cardio', 2);

# Step 5: Query with join
SELECT t.title, c.name as category, t.priority 
FROM todos t 
LEFT JOIN categories c ON t.category_id = c.id;

# Step 6: Mark as completed
UPDATE todos SET completed = 1 WHERE id = 2;

# Step 7: View completed
SELECT * FROM todos WHERE completed = 1;

.exit
```

### Exercise 2: MySQL User Management

```bash
# Task: Create a secure MySQL setup with multiple users

# Start MySQL
mysqld_safe &
mysql -u root

# Create database
CREATE DATABASE company_db;
USE company_db;

# Create tables
CREATE TABLE employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    department ENUM('IT', 'HR', 'Finance', 'Marketing'),
    salary DECIMAL(10,2),
    hire_date DATE
);

# Create users with different privileges
CREATE USER 'admin'@'localhost' IDENTIFIED BY 'Admin@123';
CREATE USER 'hr_user'@'localhost' IDENTIFIED BY 'HR@123';
CREATE USER 'readonly'@'localhost' IDENTIFIED BY 'Read@123';

# Grant privileges
GRANT ALL PRIVILEGES ON company_db.* TO 'admin'@'localhost';
GRANT SELECT, INSERT, UPDATE ON company_db.employees TO 'hr_user'@'localhost';
GRANT SELECT ON company_db.* TO 'readonly'@'localhost';
FLUSH PRIVILEGES;

# Test with different users
# Exit and login as hr_user
# mysql -u hr_user -p company_db
# Try: SELECT * FROM employees; (should work)
# Try: DROP TABLE employees; (should fail)

exit
mysqladmin -u root shutdown
```

### Exercise 3: Python SQLite Application

```python
#!/usr/bin/env python3
# Task: Create a complete contact management system

import sqlite3
from datetime import datetime

class ContactManager:
    def __init__(self, db_name='contacts.db'):
        self.conn = sqlite3.connect(db_name)
        self.cursor = self.conn.cursor()
        self.create_table()
    
    def create_table(self):
        self.cursor.execute('''
            CREATE TABLE IF NOT EXISTS contacts (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                name TEXT NOT NULL,
                phone TEXT,
                email TEXT,
                address TEXT,
                created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
            )
        ''')
        self.conn.commit()
    
    def add_contact(self, name, phone=None, email=None, address=None):
        self.cursor.execute(
            "INSERT INTO contacts (name, phone, email, address) VALUES (?, ?, ?, ?)",
            (name, phone, email, address)
        )
        self.conn.commit()
        print(f"[+] Added: {name}")
    
    def list_contacts(self):
        self.cursor.execute("SELECT * FROM contacts ORDER BY name")
        contacts = self.cursor.fetchall()
        print("\n" + "="*60)
        print("CONTACT LIST")
        print("="*60)
        for c in contacts:
            print(f"ID: {c[0]}, Name: {c[1]}, Phone: {c[2]}, Email: {c[3]}")
        print("="*60 + "\n")
    
    def search_contacts(self, keyword):
        self.cursor.execute(
            "SELECT * FROM contacts WHERE name LIKE ? OR email LIKE ?",
            (f"%{keyword}%", f"%{keyword}%")
        )
        return self.cursor.fetchall()
    
    def update_contact(self, contact_id, **kwargs):
        updates = []
        values = []
        for key, value in kwargs.items():
            if value:
                updates.append(f"{key} = ?")
                values.append(value)
        if updates:
            values.append(contact_id)
            query = f"UPDATE contacts SET {', '.join(updates)} WHERE id = ?"
            self.cursor.execute(query, values)
            self.conn.commit()
            print(f"[+] Updated contact ID: {contact_id}")
    
    def delete_contact(self, contact_id):
        self.cursor.execute("DELETE FROM contacts WHERE id = ?", (contact_id,))
        self.conn.commit()
        print(f"[+] Deleted contact ID: {contact_id}")
    
    def close(self):
        self.conn.close()

# Test the application
if __name__ == "__main__":
    app = ContactManager()
    
    # Add contacts
    app.add_contact("Rahul Kumar", "9876543210", "rahul@email.com", "Delhi")
    app.add_contact("Priya Singh", "9876543211", "priya@email.com", "Mumbai")
    app.add_contact("Amit Sharma", "9876543212", "amit@email.com", "Bangalore")
    
    # List all
    app.list_contacts()
    
    # Search
    print("Search results for 'ra':")
    for c in app.search_contacts("ra"):
        print(c)
    
    # Update
    app.update_contact(1, phone="9999999999", address="New Delhi")
    
    # Delete
    app.delete_contact(3)
    
    # Final list
    app.list_contacts()
    
    app.close()
```

### Exercise 4: Redis Caching System

```python
#!/usr/bin/env python3
# Task: Implement a caching system using Redis

import redis
import json
import time

class CacheSystem:
    def __init__(self):
        self.redis = redis.Redis(host='localhost', port=6379, decode_responses=True)
    
    def set_cache(self, key, data, ttl=300):
        """Cache data with TTL"""
        self.redis.setex(key, ttl, json.dumps(data))
        print(f"[+] Cached: {key} (TTL: {ttl}s)")
    
    def get_cache(self, key):
        """Get cached data"""
        data = self.redis.get(key)
        if data:
            print(f"[+] Cache hit: {key}")
            return json.loads(data)
        print(f"[-] Cache miss: {key}")
        return None
    
    def cache_user(self, user_id, user_data):
        """Cache user data"""
        key = f"user:{user_id}"
        self.set_cache(key, user_data, ttl=600)
    
    def get_user(self, user_id):
        """Get user from cache or return None"""
        return self.get_cache(f"user:{user_id}")
    
    def cache_api_response(self, endpoint, response, ttl=60):
        """Cache API response"""
        key = f"api:{endpoint}"
        self.set_cache(key, response, ttl)
    
    def rate_limit(self, user_id, limit=10, window=60):
        """Simple rate limiting"""
        key = f"rate:{user_id}"
        count = self.redis.get(key)
        
        if count is None:
            self.redis.setex(key, window, 1)
            return True, 1
        
        count = int(count)
        if count >= limit:
            return False, count
        
        self.redis.incr(key)
        return True, count + 1
    
    def track_page_view(self, page):
        """Track page views"""
        self.redis.incr(f"views:{page}")
    
    def get_page_views(self, page):
        """Get page view count"""
        return self.redis.get(f"views:{page}") or 0

# Test
if __name__ == "__main__":
    cache = CacheSystem()
    
    # Cache user
    cache.cache_user(1, {"name": "Rahul", "email": "rahul@email.com"})
    print(cache.get_user(1))
    
    # Rate limiting
    for i in range(12):
        allowed, count = cache.rate_limit("user:1", limit=5)
        print(f"Request {i+1}: Allowed={allowed}, Count={count}")
    
    # Page views
    for _ in range(10):
        cache.track_page_view("home")
    print(f"Home page views: {cache.get_page_views('home')}")
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: SQLite Database Locked

```bash
# Cause: Multiple processes accessing same database

# Solution 1: Close all connections
# Ensure no other process has the database open

# Solution 2: Use WAL mode
sqlite3 mydb.db "PRAGMA journal_mode=WAL;"

# Solution 3: Check for processes
lsof mydb.db 2>/dev/null || fuser mydb.db 2>/dev/null

# Solution 4: Wait and retry
sqlite3 mydb.db "PRAGMA busy_timeout=5000;"
```

### Problem 2: MySQL Won't Start

```bash
# Cause: Permission issues or corrupted data

# Solution 1: Check error log
cat ~/mysql-error.log 2>/dev/null || cat /tmp/mysql_error.log

# Solution 2: Reinitialize database
rm -rf $PREFIX/var/lib/mysql/*
mysql_install_db

# Solution 3: Check socket
ls -la /tmp/mysql.sock
rm -f /tmp/mysql.sock

# Solution 4: Start with debug
mysqld --debug

# Solution 5: Kill existing processes
pkill -9 mysqld
sleep 2
mysqld_safe &
```

### Problem 3: PostgreSQL Connection Refused

```bash
# Cause: Server not running or wrong configuration

# Solution 1: Check if server is running
pg_ctl -D ~/postgres-data status

# Solution 2: Start server
pg_ctl -D ~/postgres-data -l ~/postgres.log start

# Solution 3: Check log
cat ~/postgres.log

# Solution 4: Verify data directory
ls ~/postgres-data/

# Solution 5: Reinitialize if needed
rm -rf ~/postgres-data
initdb ~/postgres-data
```

### Problem 4: Redis Connection Error

```bash
# Cause: Server not started or port blocked

# Solution 1: Check if Redis is running
redis-cli PING

# Solution 2: Start Redis server
redis-server --daemonize yes

# Solution 3: Check port
netstat -tlnp | grep 6379

# Solution 4: Check configuration
redis-cli CONFIG GET "*"

# Solution 5: Start with specific port
redis-server --port 6379 --daemonize yes
```

### Problem 5: Python MySQL Connector Error

```bash
# Cause: Missing library or connection issues

# Solution 1: Reinstall connector
pip uninstall mysql-connector-python
pip install mysql-connector-python

# Solution 2: Check MySQL is running
pgrep mysqld

# Solution 3: Test connection manually
mysql -u root -e "SELECT 1;"

# Solution 4: Use alternative connector
pip install pymysql

# Solution 5: Check Python version
python --version
# Use appropriate connector version
```

### Problem 6: Database Out of Space

```bash
# Cause: Database files too large

# Solution 1: Check disk usage
df -h

# Solution 2: Vacuum SQLite
sqlite3 mydb.db "VACUUM;"

# Solution 3: Clean MySQL binary logs
mysql -u root -e "PURGE BINARY LOGS BEFORE NOW();"

# Solution 4: Clear Redis memory
redis-cli FLUSHALL

# Solution 5: Remove old backups
ls ~/backups/
rm ~/backups/old_backup.sql

# Solution 6: Compress old data
gzip old_database.sql
```

### Problem 7: Permission Denied Errors

```bash
# Cause: Incorrect file/directory permissions

# Solution 1: Fix MySQL data directory
chmod -R 755 $PREFIX/var/lib/mysql
chown -R $(whoami) $PREFIX/var/lib/mysql

# Solution 2: Fix PostgreSQL data
chmod 700 ~/postgres-data

# Solution 3: Fix SQLite database
chmod 644 mydb.db

# Solution 4: Check Termux permissions
termux-setup-storage

# Solution 5: Restart from correct directory
cd ~
mysqld_safe &
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Database Logos**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│  🗄️ DATABASE IN TERMUX             │
│                                    │
│  SQLite | MySQL | PostgreSQL       │
│  Redis  | MongoDB                  │
│                                    │
│  📱 Complete Guide                 │
│  [T3rmuxk1ng Logo]                 │
└────────────────────────────────────┘
```

**Option B: Comparison Style**
```
┌────────────────────────────────────┐
│  WHICH DATABASE FOR TERMUX?        │
│  ────────────────────────────────  │
│  SQLite     ✅ Lightweight         │
│  MySQL      ✅ Popular             │
│  PostgreSQL ✅ Advanced            │
│  Redis      ✅ Fast Cache          │
│  MongoDB    ✅ Flexible            │
│                                    │
│  Chapter 48 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Code Style**
```
┌────────────────────────────────────┐
│  $ mysql -u root                   │
│  > CREATE DATABASE myapp;          │
│  Query OK, 1 row affected          │
│                                    │
│  💾 DATABASE MASTERY               │
│  In Termux                         │
│                                    │
│  🔥 5 Databases | Full Guide       │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🗄️ Termux Full Course - Chapter 48: Database in Termux | Complete Guide

🔥 In this video you'll learn:
• SQLite installation aur commands
• MySQL/MariaDB setup aur user management
• PostgreSQL installation aur advanced features
• Redis caching aur data types
• MongoDB basics
• CRUD operations (Create, Read, Update, Delete)
• Python se database connectivity
• PHP + MySQL integration
• Backup aur restore strategies
• Security best practices

⏱️ Timestamps:
0:00 - Introduction
0:50 - Database Overview
3:00 - SQLite Installation & Basics
7:00 - MySQL/MariaDB Installation
12:00 - PostgreSQL Installation
15:00 - Redis Installation
17:00 - MongoDB Installation
19:00 - Python Database Connectivity
21:30 - Backup & Security
23:30 - Summary

📥 Installation Commands:
pkg install sqlite -y
pkg install mariadb -y
pkg install postgresql -y
pkg install redis -y
pip install mysql-connector-python redis

📝 GitHub Repository:
[LINK]

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #Database #MySQL #SQLite #PostgreSQL #Redis #MongoDB #T3rmuxk1ng #TermuxCourse #PythonDatabase

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly and only on systems you have permission to test.
```

### Tags List

```
termux, termux database, sqlite termux, mysql termux, 
postgresql termux, redis termux, mongodb termux, 
database termux, termux mysql, termux sqlite, 
python database termux, termux tutorial, termux course,
t3rmuxk1ng, database management, sql termux,
nosql termux, database programming, termux php mysql,
database security, database backup, crud operations termux
```

### Hashtags

```
#Termux #Database #SQLite #MySQL #PostgreSQL #Redis #MongoDB 
#TermuxDatabase #TermuxTutorial #T3rmuxk1ng #PythonDatabase 
#DatabaseManagement #SQL #NoSQL #TermuxCourse #DatabaseSecurity
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Database | Documentation |
|----------|---------------|
| SQLite | https://www.sqlite.org/docs.html |
| MySQL | https://dev.mysql.com/doc/ |
| MariaDB | https://mariadb.com/kb/ |
| PostgreSQL | https://www.postgresql.org/docs/ |
| Redis | https://redis.io/documentation |
| MongoDB | https://docs.mongodb.com/ |

### Python Database Libraries

| Library | Description |
|---------|-------------|
| sqlite3 | Built-in SQLite support |
| mysql-connector-python | Official MySQL connector |
| psycopg2 | PostgreSQL adapter |
| redis-py | Redis client |
| pymongo | MongoDB driver |
| SQLAlchemy | ORM for multiple databases |

### GUI Tools (for reference)

| Tool | Databases Supported |
|------|---------------------|
| DBeaver | All major databases |
| phpMyAdmin | MySQL/MariaDB |
| pgAdmin | PostgreSQL |
| MongoDB Compass | MongoDB |
| RedisInsight | Redis |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 49, verify:

- [ ] SQLite installed and tested with basic operations
- [ ] MySQL/MariaDB installed, server started, and user created
- [ ] PostgreSQL installed and basic commands understood
- [ ] Redis installed and caching concepts clear
- [ ] MongoDB installation options known
- [ ] CRUD operations practiced
- [ ] Python database connectivity tested
- [ ] Backup and restore commands practiced
- [ ] Security best practices understood
- [ ] At least one practice exercise completed

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 49: Proot-Distros in Termux**

- What is proot-distro?
- Installing Ubuntu on Termux
- Installing Debian, Kali Linux, Arch
- Full Linux environment setup
- Package management in proot
- Running GUI applications
- Advanced system administration

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
