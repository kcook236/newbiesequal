Kimberlys-MacBook-Air:~ kimberlycook$ psql todosdb
psql: FATAL:  database "todosdb" does not exist
Kimberlys-MacBook-Air:~ kimberlycook$ psql tododb
psql: FATAL:  database "tododb" does not exist
Kimberlys-MacBook-Air:~ kimberlycook$ psql todolistdb
psql (9.6.5)
Type "help" for help.

todolistdb=# SELECT * FROM todolist
todolistdb-# ;
ERROR:  relation "todolist" does not exist
LINE 1: SELECT * FROM todolist
                      ^
todolistdb=# SELECT * FROM todolist;
ERROR:  relation "todolist" does not exist
LINE 1: SELECT * FROM todolist;
                      ^
todolistdb=# \dt;
           List of relations
 Schema | Name  | Type  |    Owner     
--------+-------+-------+--------------
 public | todos | table | kimberlycook
(1 row)

todolistdb=# \db;
         List of tablespaces
    Name    |    Owner     | Location
------------+--------------+----------
 pg_default | kimberlycook |
 pg_global  | kimberlycook |
(2 rows)

todolistdb=# \dt;
           List of relations
 Schema | Name  | Type  |    Owner     
--------+-------+-------+--------------
 public | todos | table | kimberlycook
(1 row)

todolistdb=# SELECT * FROM todo;
ERROR:  relation "todo" does not exist
LINE 1: SELECT * FROM todo;
                      ^
todolistdb=# SELECT * FROM todos;
 todoid |   title    |               detail               | priority |         create_at          |        completed_at        
--------+------------+------------------------------------+----------+----------------------------+----------------------------
      1 | dishes     | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
      2 | litter box | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
      6 | groceries  | buy groceries from sprouts         |        1 | 2017-09-05 14:04:20.869418 |
      7 | change oil | change oil in car                  |        5 | 2017-09-05 14:08:54.241479 | 2017-09-05 14:08:54.241479
      3 | groceries  | buy groceries from sprouts         |        1 | 2017-09-05 13:57:04.818319 | 2017-09-05 14:16:25.094299
(5 rows)

todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('fix drain', 'drain is clogged', 1);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('peso surgery', 'pick up peso', 7);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('homework', 'complete daily and weekly', 3);
INSERT 0 1
todolistdb=# SELECT * FROM todos;
 todoid |    title     |               detail               | priority |         create_at          |        completed_at        
--------+--------------+------------------------------------+----------+----------------------------+----------------------------
      1 | dishes       | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
      2 | litter box   | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
      6 | groceries    | buy groceries from sprouts         |        1 | 2017-09-05 14:04:20.869418 |
      7 | change oil   | change oil in car                  |        5 | 2017-09-05 14:08:54.241479 | 2017-09-05 14:08:54.241479
      3 | groceries    | buy groceries from sprouts         |        1 | 2017-09-05 13:57:04.818319 | 2017-09-05 14:16:25.094299
      8 | fix drain    | drain is clogged                   |        1 | 2017-09-06 10:56:24.594221 |
      9 | peso surgery | pick up peso                       |        7 | 2017-09-06 10:56:44.516441 |
     10 | homework     | complete daily and weekly          |        3 | 2017-09-06 10:57:28.241871 |
(8 rows)

todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('car', 'wash car', 6);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('vacuum', 'carpet is dirty', 2);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('drink beer', 'pick up keg', 4);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('bathroom', clean bathroom', 8);
todolistdb'# INSERT INTO todos(title, detail, priority) VALUES('bathroom', 'clean bathroom', 8);
todolistdb'# INSERT INTO todos(title, detail, priority) VALUES('vacuum', 'carpet is dirty', 2);
todolistdb'# ;
todolistdb'#
todolistdb'# ^Z
[1]+  Stopped                 psql todolistdb
Kimberlys-MacBook-Air:~ kimberlycook$ psql todolistdb
psql (9.6.5)
Type "help" for help.

todolistdb=# SELECT * FROM users;
ERROR:  relation "users" does not exist
LINE 1: SELECT * FROM users;
                      ^
todolistdb=# SELECT * FROM todos;
 todoid |    title     |               detail               | priority |         create_at          |        completed_at        
--------+--------------+------------------------------------+----------+----------------------------+----------------------------
      1 | dishes       | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
      2 | litter box   | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
      6 | groceries    | buy groceries from sprouts         |        1 | 2017-09-05 14:04:20.869418 |
      7 | change oil   | change oil in car                  |        5 | 2017-09-05 14:08:54.241479 | 2017-09-05 14:08:54.241479
      3 | groceries    | buy groceries from sprouts         |        1 | 2017-09-05 13:57:04.818319 | 2017-09-05 14:16:25.094299
      8 | fix drain    | drain is clogged                   |        1 | 2017-09-06 10:56:24.594221 |
      9 | peso surgery | pick up peso                       |        7 | 2017-09-06 10:56:44.516441 |
     10 | homework     | complete daily and weekly          |        3 | 2017-09-06 10:57:28.241871 |
     11 | car          | wash car                           |        6 | 2017-09-06 10:58:11.2353   |
     12 | vacuum       | carpet is dirty                    |        2 | 2017-09-06 10:58:31.2723   |
     13 | drink beer   | pick up keg                        |        4 | 2017-09-06 10:59:10.508853 |
(11 rows)

todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('make steak', 'grill that shit', 2);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('get bday gift', 'it is evas birthday', 9);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('work out', 'need to start lifting', 1);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('budget', 'need to budget future trips', 5);
INSERT 0 1
todolistdb=# SELECT * FROM todos;
 todoid |     title     |               detail               | priority |         create_at          |        completed_at        
--------+---------------+------------------------------------+----------+----------------------------+----------------------------
      1 | dishes        | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
      2 | litter box    | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
      6 | groceries     | buy groceries from sprouts         |        1 | 2017-09-05 14:04:20.869418 |
      7 | change oil    | change oil in car                  |        5 | 2017-09-05 14:08:54.241479 | 2017-09-05 14:08:54.241479
      3 | groceries     | buy groceries from sprouts         |        1 | 2017-09-05 13:57:04.818319 | 2017-09-05 14:16:25.094299
      8 | fix drain     | drain is clogged                   |        1 | 2017-09-06 10:56:24.594221 |
      9 | peso surgery  | pick up peso                       |        7 | 2017-09-06 10:56:44.516441 |
     10 | homework      | complete daily and weekly          |        3 | 2017-09-06 10:57:28.241871 |
     11 | car           | wash car                           |        6 | 2017-09-06 10:58:11.2353   |
     12 | vacuum        | carpet is dirty                    |        2 | 2017-09-06 10:58:31.2723   |
     13 | drink beer    | pick up keg                        |        4 | 2017-09-06 10:59:10.508853 |
     14 | make steak    | grill that shit                    |        2 | 2017-09-06 11:03:04.243499 |
     15 | get bday gift | it is evas birthday                |        9 | 2017-09-06 11:03:26.975949 |
     16 | work out      | need to start lifting              |        1 | 2017-09-06 11:03:48.573793 |
     17 | budget        | need to budget future trips        |        5 | 2017-09-06 11:04:16.822908 |
(15 rows)

todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('finish client deals', 'complete contracts', 3);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('find movie', 'watch movie with eva', 10);
INSERT 0 1
todolistdb=# INSERT INTO todos(title, detail, priority) VALUES('flea meds', 'put meds on cats', 4);
INSERT 0 1
todolistdb=# SELECT * FROM todos;
 todoid |        title        |               detail               | priority |         create_at          |        completed_at        
--------+---------------------+------------------------------------+----------+----------------------------+----------------------------
      1 | dishes              | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
      2 | litter box          | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
      6 | groceries           | buy groceries from sprouts         |        1 | 2017-09-05 14:04:20.869418 |
      7 | change oil          | change oil in car                  |        5 | 2017-09-05 14:08:54.241479 | 2017-09-05 14:08:54.241479
      3 | groceries           | buy groceries from sprouts         |        1 | 2017-09-05 13:57:04.818319 | 2017-09-05 14:16:25.094299
      8 | fix drain           | drain is clogged                   |        1 | 2017-09-06 10:56:24.594221 |
      9 | peso surgery        | pick up peso                       |        7 | 2017-09-06 10:56:44.516441 |
     10 | homework            | complete daily and weekly          |        3 | 2017-09-06 10:57:28.241871 |
     11 | car                 | wash car                           |        6 | 2017-09-06 10:58:11.2353   |
     12 | vacuum              | carpet is dirty                    |        2 | 2017-09-06 10:58:31.2723   |
     13 | drink beer          | pick up keg                        |        4 | 2017-09-06 10:59:10.508853 |
     14 | make steak          | grill that shit                    |        2 | 2017-09-06 11:03:04.243499 |
     15 | get bday gift       | it is evas birthday                |        9 | 2017-09-06 11:03:26.975949 |
     16 | work out            | need to start lifting              |        1 | 2017-09-06 11:03:48.573793 |
     17 | budget              | need to budget future trips        |        5 | 2017-09-06 11:04:16.822908 |
     18 | finish client deals | complete contracts                 |        3 | 2017-09-06 11:05:07.39327  |
     19 | find movie          | watch movie with eva               |       10 | 2017-09-06 11:05:28.64179  |
     20 | flea meds           | put meds on cats                   |        4 | 2017-09-06 11:05:54.477388 |
(18 rows)

todolistdb=# SELECT title FROM todos WHERE priority = 3;
        title        
---------------------
 homework
 finish client deals
(2 rows)

todolistdb=# SELECT title FROM todos WHERE priority = 3 AND completed_at IS NULL;
        title        
---------------------
 homework
 finish client deals
(2 rows)

todolistdb=# SELECT total FROM todos WHERE completed_at IS NULL BY priority;
ERROR:  syntax error at or near "BY"
LINE 1: ...ELECT total FROM todos WHERE completed_at IS NULL BY priorit...
                                                             ^
todolistdb=# SELECT total FROM todos WHERE completed_at IS NULL ORDER BY priority;
ERROR:  column "total" does not exist
LINE 1: SELECT total FROM todos WHERE completed_at IS NULL ORDER BY ...
               ^
todolistdb=# SELECT COUNT(todoid) FROM todos WHERE completed_at IS NULL ORDER BY priority;
ERROR:  column "todos.priority" must appear in the GROUP BY clause or be used in an aggregate function
LINE 1: ...id) FROM todos WHERE completed_at IS NULL ORDER BY priority;
                                                              ^
todolistdb=# SELECT COUNT(todoid) FROM todos WHERE completed_at IS NULL ORDER BY todos.priority;
ERROR:  column "todos.priority" must appear in the GROUP BY clause or be used in an aggregate function
LINE 1: ...d) FROM todos WHERE completed_at IS NULL ORDER BY todos.prio...
                                                             ^
todolistdb=# SELECT COUNT(total title) FROM todos WHERE completed_at IS NULL ORDER BY todos.priority;
ERROR:  syntax error at or near "title"
LINE 1: SELECT COUNT(total title) FROM todos WHERE completed_at IS N...
                           ^
todolistdb=# SELECT COUNT(total title) FROM todos WHERE completed_at IS NULL ORDER BY priority DESC;
ERROR:  syntax error at or near "title"
LINE 1: SELECT COUNT(total title) FROM todos WHERE completed_at IS N...
                           ^
todolistdb=# SELECT COUNT(todoid) FROM todos WHERE completed_at IS NULL ORDER BY priority DESC;
ERROR:  column "todos.priority" must appear in the GROUP BY clause or be used in an aggregate function
LINE 1: ...d) FROM todos WHERE completed_at IS NULL ORDER BY priority D...
                                                             ^
todolistdb=# SELECT COUNT(todoid), priority FROM todos GROUP BY priority; ORDER BY priority DESC;
 count | priority
-------+----------
     2 |        3
     3 |        4
     4 |        1
     1 |       10
     1 |        9
     1 |        6
     3 |        2
     2 |        5
     1 |        7
(9 rows)

ERROR:  syntax error at or near "ORDER"
LINE 1: ORDER BY priority DESC;
        ^
todolistdb=# SELECT todoid, priority FROM todos GROUP BY priority AND completed_at IS NULL; ORDER BY priority;
ERROR:  argument of AND must be type boolean, not type integer
LINE 1: SELECT todoid, priority FROM todos GROUP BY priority AND com...
                                                    ^
ERROR:  syntax error at or near "ORDER"
LINE 1: ORDER BY priority;
        ^
todolistdb=# SELECT COUNT(todoid), priority FROM todos GROUP BY priority AND completed_at IS NULL;
ERROR:  argument of AND must be type boolean, not type integer
LINE 1: ...ELECT COUNT(todoid), priority FROM todos GROUP BY priority A...
                                                             ^
todolistdb=# SELECT COUNT(todoid), priority FROM todos GROUP BY priority,  completed_at IS NULL;
 count | priority
-------+----------
     3 |        4
     1 |        1
     1 |        6
     3 |        2
     1 |        7
     1 |        5
     1 |       10
     3 |        1
     1 |        5
     2 |        3
     1 |        9
(11 rows)

todolistdb=# SELECT COUNT(todoid), priority FROM todos GROUP BY priority,  completed_at IS NULL; ORDER BY priority;
 count | priority
-------+----------
     3 |        4
     1 |        1
     1 |        6
     3 |        2
     1 |        7
     1 |        5
     1 |       10
     3 |        1
     1 |        5
     2 |        3
     1 |        9
(11 rows)

ERROR:  syntax error at or near "ORDER"
LINE 1: ORDER BY priority;
        ^
todolistdb=# SELECT COUNT(todoid), priority FROM todos GROUP BY priority,  completed_at IS NULL, ORDER BY priority;
ERROR:  syntax error at or near "ORDER"
LINE 1: ...M todos GROUP BY priority,  completed_at IS NULL, ORDER BY p...
                                                             ^
todolistdb=# SELECT COUNT(todoid), priority FROM todos GROUP BY priority,  completed_at IS NULL, ORDER BY priority DESC;
ERROR:  syntax error at or near "ORDER"
LINE 1: ...M todos GROUP BY priority,  completed_at IS NULL, ORDER BY p...
                                                             ^
todolistdb=# SELECT COUNT(todoid), priority FROM todos GROUP BY priority,  completed_at IS NULL, ORDER BY COUNT(priority) DESC;
ERROR:  syntax error at or near "ORDER"
LINE 1: ...M todos GROUP BY priority,  completed_at IS NULL, ORDER BY C...
                                                             ^
todolistdb=# SELECT COUNT(todoid), priority FROM todos GROUP BY priority,  completed_at IS NULL; ORDER BY COUNT(priority) DESC;
 count | priority
-------+----------
     3 |        4
     1 |        1
     1 |        6
     3 |        2
     1 |        7
     1 |        5
     1 |       10
     3 |        1
     1 |        5
     2 |        3
     1 |        9
(11 rows)

ERROR:  syntax error at or near "ORDER"
LINE 1: ORDER BY COUNT(priority) DESC;
        ^
todolistdb=# SELECT * FROM todos WHERE completed_at IS NULL ORDER BY priority;
 todoid |        title        |               detail               | priority |         create_at          | completed_at
--------+---------------------+------------------------------------+----------+----------------------------+--------------
      8 | fix drain           | drain is clogged                   |        1 | 2017-09-06 10:56:24.594221 |
     16 | work out            | need to start lifting              |        1 | 2017-09-06 11:03:48.573793 |
      6 | groceries           | buy groceries from sprouts         |        1 | 2017-09-05 14:04:20.869418 |
     12 | vacuum              | carpet is dirty                    |        2 | 2017-09-06 10:58:31.2723   |
     14 | make steak          | grill that shit                    |        2 | 2017-09-06 11:03:04.243499 |
      1 | dishes              | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
     18 | finish client deals | complete contracts                 |        3 | 2017-09-06 11:05:07.39327  |
     10 | homework            | complete daily and weekly          |        3 | 2017-09-06 10:57:28.241871 |
     20 | flea meds           | put meds on cats                   |        4 | 2017-09-06 11:05:54.477388 |
      2 | litter box          | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
     13 | drink beer          | pick up keg                        |        4 | 2017-09-06 10:59:10.508853 |
     17 | budget              | need to budget future trips        |        5 | 2017-09-06 11:04:16.822908 |
     11 | car                 | wash car                           |        6 | 2017-09-06 10:58:11.2353   |
      9 | peso surgery        | pick up peso                       |        7 | 2017-09-06 10:56:44.516441 |
     15 | get bday gift       | it is evas birthday                |        9 | 2017-09-06 11:03:26.975949 |
     19 | find movie          | watch movie with eva               |       10 | 2017-09-06 11:05:28.64179  |
(16 rows)

todolistdb=# SELECT * FROM todos WHERE create_at BETWEEN 2017-08-06 AND 2017-09-06 ORDER BY priority;
ERROR:  operator does not exist: timestamp without time zone >= integer
LINE 1: SELECT * FROM todos WHERE create_at BETWEEN 2017-08-06 AND 2...
                                            ^
HINT:  No operator matches the given name and argument type(s). You might need to add explicit type casts.
todolistdb=# SELECT * FROM todos WHERE create_at BETWEEN '2017-08-07' AND '2017-09-07'  ORDER BY priority;
 todoid |        title        |               detail               | priority |         create_at          |        completed_at        
--------+---------------------+------------------------------------+----------+----------------------------+----------------------------
      3 | groceries           | buy groceries from sprouts         |        1 | 2017-09-05 13:57:04.818319 | 2017-09-05 14:16:25.094299
     16 | work out            | need to start lifting              |        1 | 2017-09-06 11:03:48.573793 |
      6 | groceries           | buy groceries from sprouts         |        1 | 2017-09-05 14:04:20.869418 |
      8 | fix drain           | drain is clogged                   |        1 | 2017-09-06 10:56:24.594221 |
      1 | dishes              | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
     12 | vacuum              | carpet is dirty                    |        2 | 2017-09-06 10:58:31.2723   |
     14 | make steak          | grill that shit                    |        2 | 2017-09-06 11:03:04.243499 |
     10 | homework            | complete daily and weekly          |        3 | 2017-09-06 10:57:28.241871 |
     18 | finish client deals | complete contracts                 |        3 | 2017-09-06 11:05:07.39327  |
     20 | flea meds           | put meds on cats                   |        4 | 2017-09-06 11:05:54.477388 |
     13 | drink beer          | pick up keg                        |        4 | 2017-09-06 10:59:10.508853 |
      2 | litter box          | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
      7 | change oil          | change oil in car                  |        5 | 2017-09-05 14:08:54.241479 | 2017-09-05 14:08:54.241479
     17 | budget              | need to budget future trips        |        5 | 2017-09-06 11:04:16.822908 |
     11 | car                 | wash car                           |        6 | 2017-09-06 10:58:11.2353   |
      9 | peso surgery        | pick up peso                       |        7 | 2017-09-06 10:56:44.516441 |
     15 | get bday gift       | it is evas birthday                |        9 | 2017-09-06 11:03:26.975949 |
     19 | find movie          | watch movie with eva               |       10 | 2017-09-06 11:05:28.64179  |
(18 rows)

todolistdb=# SELECT * FROM todos WHERE create_at BETWEEN '2017-08-07' AND '2017-09-07' AND completed_at is NULL ORDER BY priority;
 todoid |        title        |               detail               | priority |         create_at          | completed_at
--------+---------------------+------------------------------------+----------+----------------------------+--------------
      8 | fix drain           | drain is clogged                   |        1 | 2017-09-06 10:56:24.594221 |
     16 | work out            | need to start lifting              |        1 | 2017-09-06 11:03:48.573793 |
      6 | groceries           | buy groceries from sprouts         |        1 | 2017-09-05 14:04:20.869418 |
     12 | vacuum              | carpet is dirty                    |        2 | 2017-09-06 10:58:31.2723   |
     14 | make steak          | grill that shit                    |        2 | 2017-09-06 11:03:04.243499 |
      1 | dishes              | wash the dishes and dry them       |        2 | 2017-09-05 13:46:13.510268 |
     18 | finish client deals | complete contracts                 |        3 | 2017-09-06 11:05:07.39327  |
     10 | homework            | complete daily and weekly          |        3 | 2017-09-06 10:57:28.241871 |
     20 | flea meds           | put meds on cats                   |        4 | 2017-09-06 11:05:54.477388 |
      2 | litter box          | scoop the litter and throw it away |        4 | 2017-09-05 13:49:34.128024 |
     13 | drink beer          | pick up keg                        |        4 | 2017-09-06 10:59:10.508853 |
     17 | budget              | need to budget future trips        |        5 | 2017-09-06 11:04:16.822908 |
     11 | car                 | wash car                           |        6 | 2017-09-06 10:58:11.2353   |
      9 | peso surgery        | pick up peso                       |        7 | 2017-09-06 10:56:44.516441 |
     15 | get bday gift       | it is evas birthday                |        9 | 2017-09-06 11:03:26.975949 |
     19 | find movie          | watch movie with eva               |       10 | 2017-09-06 11:05:28.64179  |
(16 rows)

todolistdb=# SELECT MIN(create_ate) FROM todos WHERE completed_at IS NULL AND MIN(priority);  
ERROR:  column "create_ate" does not exist
LINE 1: SELECT MIN(create_ate) FROM todos WHERE completed_at IS NULL...
                   ^
HINT:  Perhaps you meant to reference the column "todos.create_at".
todolistdb=# SELECT * FROM todos WHERE completed_at IS NULL AND MIN(create_at)  AND MIN(priority);  
ERROR:  aggregate functions are not allowed in WHERE
LINE 1: ...ELECT * FROM todos WHERE completed_at IS NULL AND MIN(create...
                                                             ^
todolistdb=# SELECT * FROM todos GROUP BY completed_at IS NULL AND MIN(create_at)  AND MIN(priority);  
ERROR:  aggregate functions are not allowed in GROUP BY
LINE 1: ...CT * FROM todos GROUP BY completed_at IS NULL AND MIN(create...
                                                             ^
todolistdb=# SELECT * FROM todos WHERE priority = 1 ORDER BY create_at LIMIT 1;  
 todoid |   title   |           detail           | priority |         create_at          |        completed_at        
--------+-----------+----------------------------+----------+----------------------------+----------------------------
      3 | groceries | buy groceries from sprouts |        1 | 2017-09-05 13:57:04.818319 | 2017-09-05 14:16:25.094299
(1 row)

todolistdb=#
