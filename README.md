# Project1

## Project Description
Enabling Hive features with querying and optimizations where the main focal point is to understand the organization and positioning of data. Followed by querying the data, loading it into HDFS , and querying it into Hive. All of these processes are accomplished on Ubuntu.

## Technologies Used
* Ubuntu - 20.4
* Hadoop - 3.3.0
* Apache - Hive - 2.3.8

## Features
List of features ready and TODOs for future development

  * User can create databases and tables.
  * Load data into tables.
  * Query tables.
  * Save query output to files.
  
  To-do list:

  * Wow improvement to be done 1
  * Wow improvement to be done 2

## Getting Started
- Enable WSL and update to WSL2 on Windows 10
> Install Java JDK 1.8 on Windows 10
> Install Ubuntu 18+
- Install Java JDK 1.8 on Ubuntu
- Install Hadoop on Ubuntu
- Install Apache-Hive on Ubuntu
- Install Apache-Spark on ubuntu
- install Intellij Community Edition 2021
- Open Ubuntu Terminal:

  - `ssh localhost`
  - `~HADOOP_HOME/sbin/start-dfs.sh`
  - `~HADOOP_HOME/sbin/start-yarn.sh`
  - `cd`
  - `hdfs dfs -mkdir /user/project1`
  - `hdfs dfs -chmod 777 /user/project1`
  - `hdfs dfs -put <path to data>/*.txt /user/project1`
  - `beeline -u jdbc:hive2://`
  - `CREATE DATABASE project1db;`
  - `CREATE TABLE beverage_count_a(beverage STRING, count INT) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS textfile;`
  - `CREATE TABLE beverage_count_b(beverage STRING, count INT) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS textfile;`
  - `CREATE TABLE beverage_count_c(beverage STRING, count INT) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS textfile;`
  - `CREATE TABLE beverage_branch_a(beverage STRING, branch STRING) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS textfile;`
  - `CREATE TABLE beverage_branch_b(beverage STRING, branch STRING) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS textfile;`
  - `CREATE TABLE beverage_branch_c(beverage STRING, branch STRING) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS textfile;`
  - `LOAD DATA INPATH '/user/project1/Bev_ConscountA.txt' OVERWRITE INTO TABLE beverage_count_a;`
  - `LOAD DATA INPATH '/user/project1/Bev_ConscountB.txt' OVERWRITE INTO TABLE beverage_count_b;`
  - `LOAD DATA INPATH '/user/project1/Bev_ConscountC.txt' OVERWRITE INTO TABLE beverage_count_c;`
  - `LOAD DATA INPATH '/user/project1/Bev_BranchA.txt' OVERWRITE INTO TABLE beverage_branch_a;`
  - `LOAD DATA INPATH '/user/project1/Bev_BranchB.txt' OVERWRITE INTO TABLE beverage_branch_b;`
  - `LOAD DATA INPATH '/user/project1/Bev_BranchC.txt' OVERWRITE INTO TABLE beverage_branch_c;`
  - Images of what it should look like

## Usage
> What is the total number of consumers for Branch1?

- `CREATE TABLE IF NOT EXISTS branch1 AS SELECT * FROM beverage_branch_a WHERE branch = 'Branch1';`
- `INSERT INTO TABLE branch1 SELECT * FROM beverage_branch_b WHERE branch = 'Branch1';`
- `INSERT INTO TABLE branch1 SELECT * FROM beverage_branch_c WHERE branch = 'Branch1';`
- Create table of beverages consumed from branch1.
- `CREATE TABLE IF NOT EXISTS branch1_cons_count (beverage STRING, count INT);`
- `INSERT INTO TABLE branch1_cons_count select c.beverage, SUM(c.count) FROM branch1 b JOIN beverage_count_a c ON (c.beverage = b.beverage) GROUP BY c.beverage;`
- `INSERT INTO TABLE branch1_cons_count select c.beverage, SUM(c.count) FROM branch1 b JOIN beverage_count_b c ON (c.beverage = b.beverage) GROUP BY c.beverage;`
- `INSERT INTO TABLE branch1_cons_count select c.beverage, SUM(c.count) FROM branch1 b JOIN beverage_count_c c ON (c.beverage = b.beverage) GROUP BY c.beverage;`
- Sum all the beverages found in branch 1
- `SELECT SUM(count) AS `branch 1 consumers` FROM branch1_cons_count;`

## Contributors
> Here list the people who have contributed to this project. (ignore this section, if its a solo project)
## License
This project uses the following license: <license_name>.
