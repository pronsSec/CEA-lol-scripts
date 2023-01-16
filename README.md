# *dba-lol-scripts*

All mysql rn

Homesteading is a lifestyle of self-sufficiency. It is characterized by subsistence agriculture, home preservation of food, and may also involve the small scale production of textiles, clothing, and craft work for household use or sale.

---

---

---

## utf-converter.sh


Converts mysql/mariaDB databases from utf8 to utf8mb4, including all tables and fields.

Often solves for non-english db operation errors.



All given parameters are directly given to the mysql command.


Example usage: convert.sh my_database --user=my_user --password=the_password
See mysql documentation for more parameters.

-------------------------------

---

---

## check-account-enabled-mysql.sql

mysql> SELECT is_account_enabled('localhost', 'root');
* +-----------------------------------------+
* | is_account_enabled('localhost', 'root') |
* +-----------------------------------------+
* | YES                                     |
* +-----------------------------------------+

---

---

---

## enabled-events.sql

mysql> call currently_enabled(TRUE, TRUE);
 * +----------------------------+
 * | performance_schema_enabled |
 * +----------------------------+
 * |                          1 |
 * +----------------------------+
 * 1 row in set (0.00 sec)
 * 
 * +---------------+
 * | enabled_users |
 * +---------------+
 * | '%'@'%'       |
 * +---------------+
 * 1 row in set (0.01 sec)
 * 
 * +----------------------+---------+-------+
 * | objects              | enabled | timed |
 * +----------------------+---------+-------+
 * | mysql.%              | NO      | NO    |
 * | performance_schema.% | NO      | NO    |
 * | information_schema.% | NO      | NO    |
 * | %.%                  | YES     | YES   |
 * +----------------------+---------+-------+
 * 4 rows in set (0.01 sec)
 * 
 * +---------------------------+
 * | enabled_consumers         |
 * +---------------------------+
 * | events_statements_current |
 * | global_instrumentation    |
 * | thread_instrumentation    |
 * | statements_digest         |
 * +---------------------------+
 * 4 rows in set (0.05 sec)
 * 
 * +--------------------------+-------------+
 * | enabled_threads          | thread_type |
 * +--------------------------+-------------+
 * | innodb/srv_master_thread | BACKGROUND  |
 * | root@localhost           | FOREGROUND  |
 * | root@localhost           | FOREGROUND  |
 * | root@localhost           | FOREGROUND  |
 * | root@localhost           | FOREGROUND  |
 * +--------------------------+-------------+
 * 5 rows in set (0.03 sec)
 * 
 * +-------------------------------------+-------+
 * | enabled_instruments                 | timed |
 * +-------------------------------------+-------+
 * | wait/io/file/sql/map                | YES   |
 * | wait/io/file/sql/binlog             | YES   |
 * ...
 * | statement/com/Error                 | YES   |
 * | statement/com/                      | YES   |
 * | idle                                | YES   |
 * +-------------------------------------+-------+

---

---

---

## mysql-user_summary.sql

 * mysql> select * from user_summary;
 * +------+------------------+---------------+-------------+---------------------+-------------------+
 * | user | total_statements | total_latency | avg_latency | current_connections | total_connections |
 * +------+------------------+---------------+-------------+---------------------+-------------------+
 * | root |             1967 | 00:03:35.99. ..  | 109.81 ms   |                   2 |                 7 |
 * +------+------------------+---------------+-------------+---------------------+-------------------+
