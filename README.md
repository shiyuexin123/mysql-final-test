# mysql-final-test

2019-2020 mysql final test

姓名：施跃鑫

学号：17061522

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果
```sql
mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2020-04-10 08:02:12 |
+---------------------+
1 row in set (0.00 sec)
code here
```
2 组合打印自己的姓名和学号

(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果
```sql
mysql> select concat("施跃鑫+",17061522);
+-------------------------------+
| concat("施跃鑫+",17061522)    |
+-------------------------------+
| 施跃鑫+17061522               |
+-------------------------------+
1 row in set (0.13 sec)
```
3 建立如下表1和表2，写出建表语句和插入语句。

表1：其中deptno为主键
```
deptno, deptname,    loc
(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON")
```
```sql
mysql> use test;
Database changed
mysql> create table biao1(
    -> deptno int(10) primary key,
    -> deptname varchar(25),
    -> loc varchar(25)
    -> );
Query OK, 0 rows affected (0.09 sec)

mysql> insert into biao1
    -> (deptno,deptname,loc)
    -> values(10,'ACCOUNTING','NEW YORK'),(20,'RESEARCH','DALLAS'),(30,'SALES','CHICAGO'),(40,'OPERATIONS','BOSTON');
Query OK, 4 rows affected (0.03 sec)
Records: 4  Duplicates: 0  Warnings: 0
code here
```
表2：其中empno字段为主键
```
        empno, ename,    job,    MGR,   Hiredate,    sal,   comm, deptno
        (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
	(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
	(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
	(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
	(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
	(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
	(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
	(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
	(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
	(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
	(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
```
```sql
mysql> create table biao2(
    -> empno int(8) primary key,
    -> ename varchar(25),
    -> job varchar(25),
    ->  MGR int(8),
    -> Hiredate date,
    -> sal float,
    -> comm float,
    -> deptno int(8)
    -> );
Query OK, 0 rows affected (0.05 sec)

mysql> insert into biao2
    -> (empno,ename,job,MGR,Hiredate,sal,comm,deptno)
    -> values(7369,'SMITH','CLERK',7902,'1981-03-12',800.00,NULL, 20),
    ->(7499, 'ALLEN', 'SALESMAN', 7698, '1982-03-12', 1600, 300, 30),
    ->(7521, 'WARD', 'SALESMAN', 7698, '1838-03-12', 1250, 500, 30),
    ->(7566, 'JONES', 'MANAGER', 7839, '1981-03-12', 2975, NULL, 20),
    ->(7654, 'MARTIN', 'SALESMAN', 7698, '1981-01-12', 1250, 1400, 30),
    ->(7698, 'BLAKE', 'MANAGER', 7839, '1985-03-12', 2450, NULL, 10),
    ->(7788, 'SCOTT', 'ANALYST', 7566, '1981-03-12', 3000, NULL, 20),
    ->(7839, 'KING', 'PRESIDENT', NULL, '1981-03-12', 5000, NULL, 10),
    ->(7844, 'TURNER', 'SALESMAN', 7689, '1981-03-12', 1500, 0, 30),
    ->(7878, 'ADAMS', 'CLERK', 7788, '1981-03-12', 1100, NULL,20),
    ->(7900, 'JAMES', 'CLERK', 7698,'1981-03-12',  950, NULL, 30),
    ->(7902, 'FORD', 'ANALYST', 7566, '1981-03-12', 3000, NULL, 20),
    ->(7934, 'MILLER', 'CLERK', 7782, '1981-03-12', 1300, NULL, 10);
Query OK, 13 rows affected (0.02 sec)
Records: 13  Duplicates: 0  Warnings: 0
```
3.1 表2 中再插入一条记录：

`(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)`
 
例如：`(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)`
```sql
mysql> insert into biao2
    -> (empno,ename,job,MGR,Hiredate,sal,comm,deptno)
    -> values(12345,  'Zhangsan', 'sTUDENT', 7782, '2000-03-12', NULL, NULL, 10);
Query OK, 1 row affected (0.00 sec)
```
3.2 表中入职时间（Hiredate字段）最短的人。
```sql
mysql> select*from biao2 where Hiredate =(select max(Hiredate) from biao2);
+-------+----------+---------+------+------------+------+------+--------+
| empno | ename    | job     | MGR  | Hiredate   | sal  | comm | deptno |
+-------+----------+---------+------+------------+------+------+--------+
| 12345 | Zhangsan | sTUDENT | 7782 | 2000-03-12 | NULL | NULL |     10 |
+-------+----------+---------+------+------------+------+------+--------+
1 row in set (0.00 sec)
```
3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？
    答：有6种职位。本操作是选择运算。
3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；
```
 mysql> UPDATE biao2
    -> SET comm=1400
    -> WHERE ename='MILLER';
    
 mysql> select*from biao2 where comm =(select biao2(Hiredate)<1400 from biao2);
 ```
3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 
```
 mysql>select ename,sal+cmm from biao2;
 
 mysql> select count(biao2.ename) from biao2 group by ename;
 
 mysql> select sum(biao2.sal+comm)/count(biao2.ename) as biao2.ename FROM table biao2;
 ```
3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？
```
mysql> select ename,MGR form biao2;
```
3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。
```
mysql> CREATE VIEW (v_empno,v_ename,v_job,v_loc)
    -> AS SELECT * FROM (biao2.empno,biao2.ename,biao2.job,biao2.loc);
Query OK, 0 rows affected (0.00 sec)
```
答：1、视图能够简化用户的操作
2、视图使用户能以多种角度看待同一数据
3、视图对重构数据库提供了一定程度的逻辑独立性
4、视图能够对机密数据提供安全保护
5、适当利用视图可以更清晰地表达查询
3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？
```
mysql> ALTER TABLE biao1
    -> CHANGE COLUMN deptno
    -> int(8) NOT NULL;
Query OK, 0 rows affected (0.15 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
答：对deptno的某种约束,实体完整性
3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引
```
mysql>create index  ename on biao2 ;
```
答：索引就相当于一本书的目录，通过目录可以快速的找到对应的资源，缩小了扫描的范围。
3.10 将表2的 sal 字段改名为 salary
```
mysql> ALTER TABLE biao2
    -> CHANGE sal salary float;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。
```
mysql> CREATE FUNCTION get_deptno_from_empno()
    -> RETURNS int(8)
    -> RETURN
    -> (SELECT deptno FROM biao2
    -> WHERE empno=biao2.empno);
```
4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；
```
mysql> CREATE USER 'shiyuexin'@'localhost'
    -> IDENTIFIED BY '17061522';
Query OK, 0 rows affected (0.01 sec)
```
4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。
```
mysql> GRANT SELECT,INSERT,UPDATE ON biao1.ename
    -> TO 'shiyuexin'@'localhost'
    -> IDENTIFIED BY '17061522'
    -> WITH GRANT OPTION;
Query OK, 0 rows affected, 0 warning (0.01 sec)
```
4.2 显示该账号权限
```
mysql> SELECT Host,User,Select_priv,Grant_priv
    -> FROM mysql.user
    -> WHERE User='shiyuexin';
+-----------+-----------+-------------+------------+
| Host      |  User     | Select_priv | Grant_priv |
+-----------+-----------+-------------+------------+
| localhost | shiyuexin | Y           | Y          |
+-----------+-----------+-------------+------------+
1 row in set (0.01 sec)
```
4.3 `with grant option` 是什么意思。
答：`with grant option`可以将select ,update权限授权给第三方。
5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？
答：表 1 和表 2符合第一范式，不符合第二范式，因为表1表2的字段都是单一属性的，不可再分。这个单一属性由基本类型构成，包括整型、实数、字符型、逻辑型、日   期型等。 而表1表2中不存在所有非关键字段都完全依赖于任意一组候选关键字。
6 画出表 1 和表 2 所对应的 E-R 图

7 什么是外模式，什么是内模式。为什么要分成这几层？
```
答：
外模式：
外模式又称子模式或用户模式，对应于用户级。它是某个或某几个用户所看到的数据库的数据视图，是与某一来应用有关的数据的逻辑表示。外模式是从模式导出的一个子集，包含模式中允许特定用户使用的那部分数据。用户可以通过外模式描述语言来描述、定义对应于用户的数据记录(外模式)，也可以利用数据操纵语言(Data Manipulation Language，DML)对这些数据记录进自行操作。外模式反映了数据库的用户观。
内模式：
内模式又称存储模式，百对应于物理级，它是数据库中全体数据的内部表示或底层描述，是数据库最低一级的逻辑描述，它描述了数据在存度储问介质上的存储方式和物理结构，对应着实际存储在外存储介质上的数据库。内模式由内模式描述语言来描述、定义，它是数据库的存储观。
在一个数据库系统中，只有唯一的数据库， 因而作为定义 、描述数据库存储结构的内模式和定义、描述数据库逻辑结答构的模式，也是唯一的，但建立在数据库系统之上的应用则是非常广泛、多样的，所以对应的外模式不是唯一的，也不可能是唯一的。
目的：
为数据库设计了一个严谨的体系结构，数据库领域公认的标准结构是三级模式结构，它包括外模式、概念模式、内模式，有效地组织、管理数据，提高了数据库的逻辑独立性和物理独立性。用户级对应外模式，概念级对应概念模式，物理级对应内模式，使不同级别的用户对数据库形成不同的视图。
```
8 什么是ACID？
答：
ACID 一般是指数据库事务的ACID

一个事务一般是指多个操作的集合，比如插入数据库分两段插入，第二次插入错误，第一次插入操作也需要回退

ACID的翻译

1.Atomicity 原子性

2.Consistency 一致性

3.Isolation 隔离性

4.Durability 耐久性

原子性，指的是整个事务是一个独立的单元，要么操作成功，要么操作不成功

一致性，事务必须要保持和系统处于一致的状态（如果不一致会导致系统其它的方出现bug）

隔离性，事务是并发控制机制，他们的交错也需要一致性，隔离隐藏，一般通过悲观或者乐观锁实现

耐久性，一个成功的事务将永久性地改变系统的状态，所以在它结束之前，所有导致状态的变化都

       记录在一个持久的事务日志中

8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？
```sql
mysql> select @@tx_isolation;
+-----------------+
| @@tx_isolation  |
+-----------------+
| REPEATABLE-READ |
+-----------------+
1 row in set, 1 warning (0.00 sec)
```
8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？

9 有哪些场景不适合用关系型数据库？为什么？
答：
1）需要做复杂处理的数据；
2）数据量不是特别大的数据；
3）对安全性要求高的数据；
4）数据格式单一的数据；

