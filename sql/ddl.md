# SQL as Data Definition Language

## Create Tables

* CREATE TABLE &lt;name&gt; \(&lt;initialization list\(col name, type, &lt;\(not\)NULL or Key Type&gt;\)
  * CREATE TEMPORARY TABLE ..
  * table is gone when session ends
  * more settings for indexing, storage enginee, etc
  * constraints
    * UNIQUE INDEX = NORMAL INDEX + UNIQUE
    * NOT NULL
    * DEFAULT
    * CHECKa
* INSERT &lt;table&gt; \(&lt;columns&gt;\) VALUES\(&lt;values&gt;\)
* DROP TABLE IFEXISTS &lt;table&gt;

```SQL
DROP TABLE IF EXISTS `player`;
CREATE TABLE `player`  (
  `player_id` int(11) NOT NULL AUTO_INCREMENT,
  `team_id` int(11) NOT NULL,
  `player_name` varchar(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
  `height` float(3, 2) NULL DEFAULT 0.00,
  PRIMARY KEY (`player_id`) USING BTREE,
  UNIQUE INDEX `player_name`(`player_name`) USING BTREE
) ENGINE = InnoDB CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
```

in most cases, use GUIs to create data tables first \(eg. Navicat\)

### Common Constraints

* Primary Key
  * ALTER TABLE &lt;table&gt; ADD PRIMARY KEY &lt;key&gt;
  * is a kind of UNIQUE index
* Foreign Key
  * ALTER TABLE &lt;table&gt; ADD FOREIGN KEY&lt;key&gt; REFERENCES &lt;foreign table&gt;
* Index
  * CREATE INDEX,
  * ALTER TABLE &lt;table&gt; ADD INDEX &lt;index name&gt;
  * allow random access to rows to be faster

## Database Normalization

* First Normal Form
  * domain of each attribute contains only atomic\(indivisible\) value
* 2nd Normal Form
  * not have any **non-prime attribute** that is functionally dependent\(constraint between two sets of attributes\) or any proper subset of any candidate key of a relation.
* 3rd Normal Form
  * no **non-prime \(non-key\) attribute** is **transitively dependent** of any key. \(no non-prime attribute dependes on the non prime attributes, all the non prime attributes must depend on the primary key only\)

Examine common bugs/errors when designing data tables

* Redundancy
* Insert Error
* Delete Error
* Modification Error

The Tool for data table design; E-R diagram \(Entity Relationship Diagram\)