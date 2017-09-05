==> Successfully started `postgresql` (label: homebrew.mxcl.postgresql)
Kimberlys-MacBook-Air:~ kimberlycook$ psql listdb
psql: FATAL:  database "listdb" does not exist
Kimberlys-MacBook-Air:~ kimberlycook$ createdb todolistdb
Kimberlys-MacBook-Air:~ kimberlycook$ psql todolistdb
psql (9.6.5)
Type "help" for help.

todolistdb=# CREATE TABLE todos(
todolistdb(# todoID SERIAL PRIMARY KEY,
todolistdb(# title VARCHAR(255
todolistdb(# ) NOT NULL,
todolistdb(# detail VARCHAR(10000),
todolistdb(# priority INTEGER NULL DEFAULT 1,
todolistdb(# created_at timestamp DEFAULT current_timestamp,
todolistdb(# completed_at NULL timestamp
todolistdb(# );
ERROR:  syntax error at or near "NULL"
LINE 8: completed_at NULL timestamp
                     ^
todolistdb=# CREATE TABLE todos(
todolistdb(# todoID SERAL PRIMARY KEY,
todolistdb(# tital VARCHAR(255) NOT NULL,
todolistdb(# detail VARCHAR(10000),
todolistdb(# CREATE TABLE todos(
todoID SERIAL PRIMARY KEY,
title VARCHAR(255
) NOT NULL,
detail VARCHAR(10000),
priority INTEGER NULL DEFAULT 1,
created_at timestamp DEFAULT current_timestamp,
completed_at NULL timestamp
);
todolistdb(#
todolistdb(# );
ERROR:  syntax error at or near "CREATE"
LINE 5: CREATE TABLE todos(
        ^
todolistdb=# CREATE TABLE todos(
todolistdb(# todoID SERIAL PRIMARY KEY,
todolistdb(# title VARCHAR(255) NOT NULL,
todolistdb(# detail VARCHAR(1000),
todolistdb(# priority INTEGER NULL DEFAULT 1,
todolistdb(# create_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
todolistdb(# completed at TIMESTAMP
todolistdb(# );
ERROR:  syntax error at or near "completed"
LINE 7: completed at TIMESTAMP
        ^
todolistdb=# CREATE TABLE todos(
todolistdb(# todoID SERIAL PRIMARY KEY,
todolistdb(# title VARCHAR(255) NOT NULL,
todolistdb(# detail VARCHAR(1000),
todolistdb(# priority INTEGER NULL DEFAULT 1,
todolistdb(# create_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
todolistdb(# completed_at TIMESTAMP
todolistdb(# );
ERROR:  syntax error at or near "completed_at"
LINE 7: completed_at TIMESTAMP
        ^
todolistdb=# CREATE TABLE todos(
todolistdb(# todoID SERIAL PRIMARY KEY,
todolistdb(# title VARCHAR(255) NOT NULL,
todolistdb(# detail VARCHAR(1000),
todolistdb(# priority INTEGER NULL DEFAULT 1,
todolistdb(# create_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
todolistdb(# completed_at TIMESTAMP
todolistdb(# );
CREATE TABLE
todolistdb=# \dt
           List of relations
 Schema | Name  | Type  |    Owner     
--------+-------+-------+--------------
 public | todos | table | kimberlycook
(1 row)

todolistdb=# \db
         List of tablespaces
    Name    |    Owner     | Location
------------+--------------+----------
 pg_default | kimberlycook |
 pg_global  | kimberlycook |
(2 rows)

todolistdb=# \dt
           List of relations
 Schema | Name  | Type  |    Owner     
--------+-------+-------+--------------
 public | todos | table | kimberlycook
(1 row)

todolistdb=# SELECT * FROM todos
todolistdb-# INSERT INTO todos (title, detail, priority) VALUES (dishes, wash the dishes, 2);
ERROR:  syntax error at or near "INTO"
LINE 2: INSERT INTO todos (title, detail, priority) VALUES (dishes, ...
               ^
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES(dishs, wash the dishes and dry them, 2);
ERROR:  syntax error at or near "the"
LINE 1: ...todos(title, detail, priority) VALUES(dishs, wash the dishes...
                                                             ^
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES(dishes, wash dishes and dry them, 2);
ERROR:  syntax error at or near "dishes"
LINE 1: ...odos(title, detail, priority) VALUES(dishes, wash dishes and...
                                                             ^
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('dishes', 'wash the dishes and dry them', 2);
INSERT 0 1
todolistdb=# \dt
           List of relations
 Schema | Name  | Type  |    Owner     
--------+-------+-------+--------------
 public | todos | table | kimberlycook
(1 row)

todolistdb=# \dt todos
           List of relations
 Schema | Name  | Type  |    Owner     
--------+-------+-------+--------------
 public | todos | table | kimberlycook
(1 row)

todolistdb=# \db
         List of tablespaces
    Name    |    Owner     | Location
------------+--------------+----------
 pg_default | kimberlycook |
 pg_global  | kimberlycook |
(2 rows)

todolistdb=# SELECT * FROM todos
todolistdb-# INSERT INTO todos(title, detail, priority) VALUES('litter box', 'scoop the litter and throw it away', 4);
ERROR:  syntax error at or near "INTO"
LINE 2: INSERT INTO todos(title, detail, priority) VALUES('litter bo...
               ^
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('litter box', 'scoop the litter and throw it away' 4);
ERROR:  syntax error at or near "4"
LINE 1: ...ALUES('litter box', 'scoop the litter and throw it away' 4);
                                                                    ^
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('litter box', 'scoop the litter and throw it away', 4);
INSERT 0 1
todolistdb=# \dt todos
           List of relations
 Schema | Name  | Type  |    Owner     
--------+-------+-------+--------------
 public | todos | table | kimberlycook
(1 row)

todolistdb=# dt
todolistdb-# /dt
todolistdb-# \dt
           List of relations
 Schema | Name  | Type  |    Owner     
--------+-------+-------+--------------
 public | todos | table | kimberlycook
(1 row)

todolistdb-# \dc
               List of conversions
 Schema | Name | Source | Destination | Default?
--------+------+--------+-------------+----------
(0 rows)

todolistdb-# \dr
todolistdb-# SELECT * FROM todos;
ERROR:  syntax error at or near "dt"
LINE 1: dt
        ^
todolistdb=# \dt;
           List of relations
 Schema | Name  | Type  |    Owner     
--------+-------+-------+--------------
 public | todos | table | kimberlycook
(1 row)

todolistdb=# SELECT * FROM todos;
 todoid |   title    |               detail               | priority |         create_at          | completed_at
--------+------------+------------------------------------+----------+----------------------------+--------------
      1 | dishes     | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
      2 | litter box | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
(2 rows)

todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('groceries', 'buy groceries from sprouts', 1)
todolistdb-# ;
INSERT 0 1
todolistdb=# SELECT * FROM todos;
 todoid |   title    |               detail               | priority |         create_at          | completed_at
--------+------------+------------------------------------+----------+----------------------------+--------------
      1 | dishes     | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
      2 | litter box | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
      3 | groceries  | buy groceries from sprouts         |        1 | 2017-09-05 13:57:04.818319 |
(3 rows)

todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he's shedding like crazy');
todolistdb'# ;
todolistdb'# INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he's shedding like crazy', 3);
ERROR:  syntax error at or near "s"
LINE 1: ...) VALUES('brush calvin', 'brush calvin because he's shedding...
                                                             ^
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he's shedding like crazy');
;
INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he sheds', 3);
todolistdb'# INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he sheds', 3);
todolistdb'# SELECT * FROM todos;
todolistdb'# INSERT INTO todos(title, detail, priority) VALUES('groceries', 'buy groceries from sprouts', 1);
todolistdb'# \dt;
todolistdb'# SELECT * FROM todos;
todolistdb'# INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'calvin is shedding', 3);
todolistdb'# INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he's shedding like crazy');
;
INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he's shedding like crazy', 3);
ERROR:  syntax error at or near "s"
LINE 1: ...) VALUES('brush calvin', 'brush calvin because he's shedding...
                                                             ^
todolistdb'# INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he's shedding like crazy');
;
INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he sheds', 3);
INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he sheds', 3);
SELECT * FROM todos;
INSERT INTO todos(title, detail, priority) VALUES('groceries', 'buy groceries from sprouts', 1);
\dt;
SELECT * FROM todos;
INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'calvin is shedding', 3);
INSERT INTO todos(title, detail, priority) VALUES('brush calvin', 'brush calvin because he sheds', 3);
ERROR:  syntax error at or near "s"
LINE 1: ...) VALUES('brush calvin', 'brush calvin because he's shedding...
                                                             ^
INSERT 0 1
INSERT 0 1
 todoid |    title     |               detail               | priority |         create_at          | completed_at
--------+--------------+------------------------------------+----------+----------------------------+--------------
      1 | dishes       | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
      2 | litter box   | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
      3 | groceries    | buy groceries from sprouts         |        1 | 2017-09-05 13:57:04.818319 |
      4 | brush calvin | brush calvin because he sheds      |        3 | 2017-09-05 14:04:20.860985 |
      5 | brush calvin | brush calvin because he sheds      |        3 | 2017-09-05 14:04:20.865005 |
(5 rows)

INSERT 0 1
No matching relations found.
\dt;: extra argument "*" ignored
\dt;: extra argument "FROM" ignored
\dt;: extra argument "todos;" ignored
\dt;: extra argument "INSERT" ignored
\dt;: extra argument "INTO" ignored
\dt;: extra argument "todos(title," ignored
\dt;: extra argument "detail," ignored
\dt;: extra argument "priority)" ignored
\dt;: extra argument "VALUES(brush calvin," ignored
\dt;: extra argument "calvin is shedding," ignored
\dt;: extra argument "3);" ignored
\dt;: extra argument "INSERT" ignored
\dt;: extra argument "INTO" ignored
\dt;: extra argument "todos(title," ignored
\dt;: extra argument "detail," ignored
\dt;: extra argument "priority)" ignored
\dt;: extra argument "VALUES(brush calvin," ignored
\dt;: extra argument "brush calvin because he sheds," ignored
\dt;: extra argument "3);" ignored
todolistdb=# INSERT INTO todos(title, detail, priority, completed_at) VALUES('change oil', 'change oil in car', 5, 2017-09-05 14:05:20.938448);
ERROR:  syntax error at or near "14"
LINE 1: ...('change oil', 'change oil in car', 5, 2017-09-05 14:05:20.9...
                                                             ^
todolistdb=# INSERT INTO todos(title, detail, priority, completed_at) VALUES('change oil', 'change oil in car', 5, 2017-09-05);
ERROR:  column "completed_at" is of type timestamp without time zone but expression is of type integer
LINE 1: ..._at) VALUES('change oil', 'change oil in car', 5, 2017-09-05...
                                                             ^
HINT:  You will need to rewrite or cast the expression.
todolistdb=# INSERT INTO todos(title, detail, priority, completed_at) VALUES('change oil', 'change oil in car', 5, 2017-09-05 14:06);
ERROR:  syntax error at or near "14"
LINE 1: ...UES('change oil', 'change oil in car', 5, 2017-09-05 14:06);
                                                                ^
todolistdb=# INSERT INTO todos(title, detail, priority, completed_at) VALUES('change oil', 'change oil in car', 5, current_timestamp);
INSERT 0 1
todolistdb=# UPDATE todos SET completed_at = current_timestamp WHERE todoid = 3;
UPDATE 1
todolistdb=# SELECT * FROM todos;
 todoid |    title     |               detail               | priority |         create_at          |        completed_at        
--------+--------------+------------------------------------+----------+----------------------------+----------------------------
      1 | dishes       | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
      2 | litter box   | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
      4 | brush calvin | brush calvin because he sheds      |        3 | 2017-09-05 14:04:20.860985 |
      5 | brush calvin | brush calvin because he sheds      |        3 | 2017-09-05 14:04:20.865005 |
      6 | groceries    | buy groceries from sprouts         |        1 | 2017-09-05 14:04:20.869418 |
      7 | change oil   | change oil in car                  |        5 | 2017-09-05 14:08:54.241479 | 2017-09-05 14:08:54.241479
      3 | groceries    | buy groceries from sprouts         |        1 | 2017-09-05 13:57:04.818319 | 2017-09-05 14:16:25.094299
(7 rows)

todolistdb=# SELECT title FROM todos WHERE completed_at IS NULL;
    title     
--------------
 dishes
 litter box
 brush calvin
 brush calvin
 groceries
(5 rows)

todolistdb=# SELECT title FROM todos WHERE priority => 1;
ERROR:  syntax error at or near "=>"
LINE 1: SELECT title FROM todos WHERE priority => 1;
                                               ^
todolistdb=# SELECT title FROM todos WHERE priority = 1;
   title   
-----------
 groceries
 groceries
(2 rows)

todolistdb=# SELECT title FROM todos WHERE priority > 1;
    title     
--------------
 dishes
 litter box
 brush calvin
 brush calvin
 change oil
(5 rows)

todolistdb=# DELETE FROM todos WHERE priority = 3;
DELETE 2
todolistdb=#
