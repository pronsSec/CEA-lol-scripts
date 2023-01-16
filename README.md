# *dba-lol-scripts*
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
