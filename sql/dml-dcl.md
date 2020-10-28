# Data Manipulation and Controls in SQL

- [Data Manipulation and Controls in SQL](#data-manipulation-and-controls-in-sql)
  - [Commands to manipulate data](#commands-to-manipulate-data)
  - [Transactions](#transactions)
    - [Commands](#commands)
    - [auto commit](#auto-commit)
    - [Isolation level](#isolation-level)
  - [cursor](#cursor)
  - [Connect with Python](#connect-with-python)
    - [API Standards](#api-standards)
      - [ORM Framework](#orm-framework)

## Commands to manipulate data

- Alter <Table_name>
  - add \<col\> <col_type>
  - ADD PRIMARY KEY \<col\>
    - ADD FROEIGN KEY ... references ...
  - drop \<col\>
  - change \<old_col\> \<new_col>
  - modify \<col\> \<col_type\>
- UPDATE <table> SET <col> = ... WHERE ...
- DELETE FROM <table> WHERE ...

## Transactions

- Automicity
- [Consistency](https://en.wikipedia.org/wiki/ACID): maintain consistency for every roll back
- Isolation: not affect by other transactions
- Durability

Transactions is supported by Oracle, some engines in MySQL\(SHOW ENGINES\)

### Commands

- START TRANSACTION or BEGIN
  - explicitly start a transaction - multiple sentences go toghether
- COMMIT
- ROLLBACK \[TO &lt;savepoint&gt;\]
- SAVEPOINT
- RELEASE SAVEPOINT
- SET TRANSACTION
  - different isolation levels

### auto commit

supported by MySQL

```SQL

mysql> set autocommit =0;  //关闭自动提交
mysql> set autocommit =1;  //开启自动提交

```

### Isolation level

in SQL 92， [Isolation](https://en.wikipedia.org/wiki/Isolation_%28database_systems%29#:~:text=A%20dirty%20read%20%28aka%20uncommitted,transaction%20and%20not%20yet%20committed.)

- dirty read: read uncommited transactions
- nonrepeatable read: other transactions changed/deleted data between two reads
- phantom read: more data was added between reads

| Isolation level | dirty read | nonrepeatable read | phantom read |
| :--- | :--- | :--- | :--- |
| READ UNCOMMITED | T | T | T |
| READ COMMITED | F | T | T |
| REPEATABLE READ | F | F | T |
| SERIALIZABLE | F | F | F |

## cursor

```SQL
// 1.)
// MySQL, SQL Server, DB2, Maria DB
DECLARE cursor_name CURSOR FOR select_statement

// Oracle, PostgreSQL
DECLARE cursor_name CURSOR IS select_statement

// 2.)
OPEN cursor_name

// 3.)
FETCH cursor_name INTO var_name ...

// 4.)
CLOSE cursor_name

// 5.)
DEALLOCATE cursor_namec 
```

- cursor overflow: reached EOF

```SQL
dd
    CREATE PROCEDURE `alter_attack_growth`()
    BEGIN
           -- 创建接收游标的变量
           DECLARE temp_id INT;  
           DECLARE temp_growth, temp_max, temp_start, temp_diff FLOAT;  

           -- 创建结束标志变量  
           DECLARE done INT DEFAULT false;
           -- 定义游标     
           DECLARE cur_hero CURSOR FOR SELECT id, attack_growth, attack_max, attack_start FROM heros;
           -- 指定游标循环结束时的返回值  
           DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = true;  

           OPEN cur_hero;  
           FETCH cur_hero INTO temp_id, temp_growth, temp_max, temp_start;
           REPEAT
                         IF NOT done THEN
                                SET temp_diff = temp_max - temp_start;
                                IF temp_growth < 5 THEN
                                       IF temp_diff > 200 THEN
                                              SET temp_growth = temp_growth - 1.1;
                                       ELSEIF temp_diff >= 150 AND temp_diff <=200 THEN
                                              SET temp_growth = temp_growth - 1.08;
                                       ELSEIF temp_diff < 150 THEN
                                              SET temp_growth = temp_growth - 1.07;
                                       END IF;                       
                                ELSEIF temp_growth >=5 AND temp_growth <=10 THEN
                                       SET temp_growth = temp_growth - 1.05;
                                END IF;
                                UPDATE heros SET attack_growth = ROUND(temp_growth,3) WHERE id = temp_id;
                         END IF;
           FETCH cur_hero INTO temp_id, temp_growth, temp_max, temp_start;
           UNTIL done = true END REPEAT;

           CLOSE cur_hero;
    END
```

## Connect with Python

### API Standards

Follow [Python DB API](https://www.python.org/dev/peps/pep-0249/) Standards

- mysql-connector
- MySQLdb
- mysqlclient
- PyMySQL

#### ORM Framework

- SQLAlchemy
  - session
  - datatypes
- Django
  - models
- peewee

Mapping

- Column &lt;--&gt; Table
- Column instance -&gt; row
- Attributes -&gt; SQL fields