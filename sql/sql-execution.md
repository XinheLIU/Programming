# SQL Execution

Using Oracle as example, several steps

1. Grammar Check
2. Semantic Check: check object to be visited exists
3. Entitlement Check
4. **Shared Pool Check**: Executed expressions are cached \(using hashing\) here. If found, go to executor directly, "**soft parsing**"

   * bind to variable can optimize the performance

     * ```SQL
       SQL> select * from player where player_id = :player_id;
       ```

5. Optimizer: use parse tree to parse the sentence
6. Executor

![Oracle](/assets/Oracle.png)

MySQL uses a layered system, SQL layer is decoupled from storage methods. Sentences are cached similarly

* Connection Layer
* SQL Layer
* Storage Engine Layer \(use add-in, which is different from Oracle\)
  * InnoDB, MyISAM, Memory, NDB, Archive
  * support different functionalities such as row lock, events, etc
  * can choose different Engine for different table

The common logic is: parser -&gt; Optimizer -&gt; Executor

![](/assets/MySQL.png)

## Profile SQL

* use set profiling=1 to turn on profile

## SELECT Sentence Execution

Sequence in

SELECT FROM WHERE GROUP BY HAVING ORDER BY

The **Complier** Read like

**FROM -&gt; WHERE -&gt; GROUP BY -&gt; HAVING -&gt; SELECT -&gt; DISTINCT -&gt; ORDER BY**

* FROM
  * when two tables in FROM, complier will do CROSS JOIN \(Cartesian product\) to get virtual table v1-1
  * use ON to filter selected results, virtual table v1-2
  * add external rows used by JOIN commands,virtual table v1-3
* WHERE
  * vt1 filter to get vt2
* GROUP BY and HAVING 
  * virtual table vt3 and vt4
* SELECT and DISTINCT to get data
  * wildcard is nor recommended in production
* sort data, etc