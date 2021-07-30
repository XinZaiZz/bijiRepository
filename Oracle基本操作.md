### Oracle

![u](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722090829055.png)

####Oracle数据库概念

Oracle Database，又名Oracle RDBMS，或简称Oracle。是[甲骨文公司](https://baike.baidu.com/item/甲骨文公司/430115)的一款[关系数据库管理系统](https://baike.baidu.com/item/关系数据库管理系统/11032386)。它是在数据库领域一直处于领先地位的产品。可以说Oracle数据库系统是目前世界上流行的[关系数据库](https://baike.baidu.com/item/关系数据库/1237340)管理系统，系统[可移植性](https://baike.baidu.com/item/可移植性/6931884)好、使用方便、功能强，适用于各类大、中、小[微机](https://baike.baidu.com/item/微机/5511409)环境。它是一种高效率的、可靠性好的、适应高[吞吐量](https://baike.baidu.com/item/吞吐量/157092)的数据库方案。

####系统简介

ORACLE[数据库系统](https://baike.baidu.com/item/数据库系统)是美国ORACLE公司（[甲骨文](https://baike.baidu.com/item/甲骨文/471435)）提供的以[分布式数据库](https://baike.baidu.com/item/分布式数据库)为核心的一组软件产品，是目前最流行的客户/服务器([CLIENT/SERVER](https://baike.baidu.com/item/CLIENT%2FSERVER/1504488))或[B/S](https://baike.baidu.com/item/B%2FS/219020)[体系结构](https://baike.baidu.com/item/体系结构)的数据库之一。比如SilverStream就是基于数据库的一种[中间件](https://baike.baidu.com/item/中间件/452240)。ORACLE数据库是目前世界上使用最为广泛的[数据库管理系统](https://baike.baidu.com/item/数据库管理系统)，作为一个通用的数据库系统，它具有完整的[数据管理](https://baike.baidu.com/item/数据管理)功能；作为一个关系数据库，它是一个完备关系的产品；作为分布式数据库它实现了[分布式处理](https://baike.baidu.com/item/分布式处理)功能。但它的所有知识，只要在一种机型上学习了ORACLE知识，便能在各种类型的机器上使用它。

Oracle数据库最新版本为Oracle Database 20c。Oracle数据库12*c* 引入了一个新的多承租方架构，使用该架构可轻松部署和管理数据库云。此外，一些创新特性可最大限度地提高资源使用率和灵活性，如Oracle Multitenant可快速整合多个数据库，而Automatic Data Optimization和Heat Map能以更高的密度压缩数据和对数据分层。这些独一无二的技术进步再加上在可用性、安全性和大数据支持方面的主要增强，使得Oracle数据库12*c* 成为私有云和公有云部署的理想平台。

#### Oracle基本数据类型：

#####字符类型

字符串数据类型还可以依据存储空间分为固定长度类型（CHAR/NCHAR) 和可变长度类型（VARCHAR2/NVARCHAR2)两种.
固定长度：是指虽然输入的字段值小于该字段的限制长度，但是实际存储数据时，会先自动向右补足空格后，才将字段值的内容存储到数据块中。

可变长度：是指当输入的字段值小于该字段的限制长度时，直接将字段值的内容存储到数据块中，而不会补上空白，这样可以节省数据块空间。

char(size [BYTE | CHAR]):默认1字节，n值最大为2000.定长字符串，会用空格填充来达到其最大长度。如非null的char(n)总是包含n个字节信息。可以指定它存储字节或字符，例如 CHAR(12 BYTYE) CHAR(12 CHAR)

nchar(n):默认1字符，最大存储内容2000字节.这是一个包含Unicode格式数据的定长字符串。它的最大长度取决于国家字符集。

varchar2(n BYTE/CHAR):最大长度必须指定，至少为1字节或者1字符，n值最大为4000.长度为n个字节的可变长度且非Unicode的字符数据。

varchar(n):VARCHAR数据类型目前是VARCHAR2的同义词

nvarchar2(n)：最大长度必须指定，最大存储内容4000字节.包含n个字符的可变长度Unicode字符数据.

例：我和coffee
  char字段占n个字节的存储空间
  varchar字段占2\*2+6=10个字节的存储空间
  nvarchar字段占8\*2=16个字节的存储空间
 字段值只是英文可选择varchar2，而字段值存在较多的双字节（中文等）字符时使用nvarchar2

##### 数字类型

NUMBER(p[,s]):1-22字节。P(Precison)取值范围1到38,S(Scale)取值范围-84到127.可以存放数据范围为10^130~10^126（不包含此值).正值s为小数位数，负值s表示四舍五入到小数点左部多少位。
例：123.89 
NUMBER(6,1) 123.9
NUMBER(6,-1) 120

INTEGER类型：INTEGER是NUMBER的子类型，它等同于NUMBER（38,0），用来存储整数。若插入、更新的数值有小数，则会被四舍五入。

BINARY_FLOAT：每个BINARY_FLOAT的值需要5个字节，其中有一长度字节。32位单精度浮点数类型。符号位1位，指数位8位，尾数位23位

BINARY_DOUBLE：9字节，其中有一长度字节。64位双精度浮点数类型

##### 日期类型

DATE：其中总包含7个属性，包括：世纪、年、月、日期、小时、分钟和秒。一般占用7个字节的存储空间

TIMESTAMP [(fractional_seconds_precision)]（时间戳）：一个7字节或12字节的定宽日期/时间数据类型。fractional_seconds_precision为Oracle存储秒值小数部分位数，默认为6，可选值为0到9。没有时间区

TIMESTAMP [(fractional_seconds_precision)] WITH TIME ZONE：使用UTC，这是TIMESTAMP类型的变种，它包含了时区偏移量的值

TIMESTAMP [(fractional_seconds_precision)] WITH LOCAL TIME ZONE：存时使用数据库时区，取时使用回话的时区

INTERVAL YEAR [(year_precision)] TO MONTH：包含年、月的时间间隔类型。year_precision是年字段的数字位数，默认为2，可取0至9

INTERVAL DAY [(day_precision)]TO SECOND [(fractional_seconds_precision)]：day_precision是月份字段的数字位数，默认为2，可取0至9

##### LOB大对象类型

CLOB：最大为(4GB-1)*数据库块大小，存储单字节或者多字节字符数据，支持事务处理。主要用于存储大型英文字符

NCLOB：最大为(4GB-1)*数据库块大小，存储Unicode数据。支持事务处理。主要用于存储大型非英文字符

BLOB：最大为(4GB-1)*数据库块大小，存储非结构化二进制数据，支持事务处理。可以被认为是没有字符集语义的比特流，主要存储图像、声音、视频等文件。

BFILE：LOB地址指向文件系统上的一个二进制文件，维护目录和文件名。不参与事务处理。只支持只读操作。

##### 其他类型

LONG：最大为2GB，变长类型，存储字符串。与VARCHAR2 或CHAR 类型一样，存储在LONG 类型中的文本要进行字符集转换.ORACLE建议开发中使用CLOB替代LONG类型。支持LONG 列只是为了保证向后兼容性。CLOB类型比LONG类型的限制要少得多。

RAW(n)：最大2000字节，n为字节数，必须指定n。变长类型，字符集发生变化时不会改变值。

LONG RAW:最大为2GB,变长类型，不建议使用，建议转化为BLOB类型，字符集发生变化时不会改变值。

ROWID:10字节.代表记录的地址。显示为18位的字符串。用于定位数据库中一条记录的一个相对唯一地址值。通常情况下，该值在该行数据插入到数据库表时即被确定且唯一。ROWID它是一个伪列，它并不实际存在于表中

UROWID:UROWID(universal rowid)类型可以存储物理，逻辑或外来(non-Oracle)ROWID

##### SQL语句分为一下三种类型：

DML：Data Manipulation Language 数据操纵语言（增删改查）可以回滚

DDL：Data Definition Language 数据定义语言（创建表，删除表等）不能回滚

DCL：Data Control Language 数据控制语言（访问授权等）

#####SQL语句与SQL * PLUS差异

sql：一种语言，ANSI标准，关键字不能缩写，使用语句控制数据库中的表的定义信息和表中数据；

sql*plus：一种环境，oracle的特性之一，关键字可以缩写，命令不能改变数据库中的数据的值，集中运行。

#####SQL语句中不区分大小写，但如果算作字符串的话严格区分大小写。'\\' 表示一个转义字符。

#### Oracle安装

将下载的两个Oracle压缩包同时解压，到一个database文件中：

![image-20210722125623406](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722125623406.png)

点击setup.exe

去掉版本更新，直接下一步，输入容易记住的口令，直接安装并完成。

![image-20210722125845845](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722125845845.png)

修改口令管理，将scott管理员的口令设为tiger。

打开SQL plus 输入select sysdate from dual;如果显示当前系统时间则前面全部配置完毕。

![image-20210722130034510](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722130034510.png)

#### 卸载Oracles数据库：

直接在开始菜单下的程序中Oracle-Ora_Db11g_home1中的卸载软件，并在卸载提示过程中用控制台输入，再删除注册表中HKEY_LOCAL_MACHINE下的SOFTWARE中ORACLE文件夹，再在同级目录SYSTEM下services中删除Oracle11文件夹，再删除C盘下program file中的ORACLE以及安装本地的文件即可完整卸载。

#### PLSQL连接数据库：

Oracle安装后配置相应环境变量：

![image-20210722153455234](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722153455234.png)

![image-20210722153516160](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722153516160.png)

第一次启动plsqldev选择取消，在工具-->首选项-->添加主目录名和OCI库即可成功登陆

![image-20210722153646579](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722153646579.png)

点击左上角打开命令窗口：

![image-20210722153902662](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722153902662.png)

依次使用`@F:\实习学习笔记\尚硅谷Oracle教程\[尚硅谷]_宋红康_oracle_sql_plsql课件_章节练习_资料\2.数据表文件\del_data.sql`

` @F:\实习学习笔记\尚硅谷Oracle教程\[尚硅谷]_宋红康_oracle_sql_plsql课件_章节练习_资料\2.数据表文件\hr_cre.sql`

` @F:\实习学习笔记\尚硅谷Oracle教程\[尚硅谷]_宋红康_oracle_sql_plsql课件_章节练习_资料\2.数据表文件\hr_popul.sql`导入预先准备需要学习的表

![image-20210722154239694](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722154239694.png)

表结构：

![image-20210722174036014](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722174036014.png)

测试 `select * from employees;`成功查出：

![image-20210722154338548](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722154338548.png)



##### 连接成功

#### DBMS：

##### 实例：

一个Oracle实例有一些列的后台进程和内存结构组成。一个数据库可以由n个实例

##### 用户

用户是在实例下建立的，不同实例可以建相同名字的用户。

##### 表空间

表空间是Oracle对物理数据库上相关数据文件的逻辑映射，一个数据库在逻辑上被划分成一到若干个表空间，每个表空间包含了再逻辑上相关联的一组结构。每个数据库至少有一个表空间，每个表空间由同一磁盘上的一个或多个文件组成，这些文件叫数据文件，一个数据文件只能属于一个表空间。

##### 对象：

常见的数据库对象：

表：基本的数据存储集合，由行和列组成

视图：从表中抽出的逻辑上相关的数据集合

序列：提供有规律的数值

索引：提高查询效率

同义词：给对象起别名

在命令窗口中`ed + enter`打开文本编辑器：

![image-20210722161336286](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722161336286.png)

创建一张表：

![image-20210722161825300](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722161825300.png)

点击确定，输入`/`后回车即可执行命令。

#### 基本SQL-SELECT语句

######在SQL中字符串用单引号，只有别名用的是双引号

`desc employees;` 查看employees表中属性列：

`select * from user_tables;` 查看用户创建有哪些表



![image-20210722174155081](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722174155081.png)

`select employee_id[列名],first_name,last_name from employees[表名];` 用于查询表中指定列。

![image-20210722174742827](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722174742827.png)

日期和数字是可以进行算术运算的

如计算每个人每年的工资：`select last_name,salary*12+5000 from employees;`

![image-20210722175138314](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722175138314.png)

计算日期：`select sysdate,sysdate+2,sysdate-3 from dual;` 其中dual表示伪表，任何查询都是需要用from [表名]关键字

![image-20210722175446423](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722175446423.png)

###### 注意：日期只能加减，不能作乘除

###### 空值不同于“0”凡是空值参与的运算，结果都为空（null）

###### 列或者表都可以取别名（空格或者as，或者""双引号不会全部变成大写和空格）

`select employee_id id,last_name 名,12*salary 年工资 from employees;`



![image-20210722180318376](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722180318376.png)

##### 连接符‘||’

` select last_name||'的工作是'||job_id from employees;` 

![image-20210722185700965](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722185700965.png)

` select '编号'||employee_id||'的名字全称是'||first_name||'  '||last_name from employees;`(其中可以对查询列起别称)

![image-20210722185928727](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722185928727.png)

###### distinct关键字用于去除重复值

`select distinct department_id from employees;` 查询所有部门id

![image-20210722190549875](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722190549875.png)

条件查询（过滤表）

`select employee_id from employees where employee_id>200` 

![image-20210722202205425](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722202205425.png)

`select employee_id,first_name,department_id from employees where department_id = 100;`

`select employee_id,first_name,department_id from employees where first_name = 'Nancy';`

![image-20210722203020052](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722203020052.png)

如果查询条件是日期的话，可以用to_char([属性],'yyyy-MM-dd')方法进行格式转换

` select employee_id,first_name,department_id from employees where to_char(hire_date,'yyyy-MM-dd') = '1996-03-04';`

`select hire_date from employees where to_char(hire_date,'yyyy,MM,dd') > '1996-03-04';`(也可对时间进行比较运算查询)

`select employee_id as "id",salary as "工资" from employees where salary>=8000 and salary<10000;`

######如果用between and 关键字会包含边界

![image-20210722205112021](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722205112021.png)

###### in关键字

`select department_id from employees where department_id in (70,80,90);`

![image-20210722205333178](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722205333178.png)

###### 模糊查询（‘%’代表一位或多位，’_‘表示一位）

查询员工中含有字符a的员工：

`select last_name from employees where last_name like '%a%'; `

![image-20210722210416698](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210722210416698.png)

查询名字中带有下划线的id和name:

` select employee_id,last_name from employees where last_name like '%\_%'escape '\';`

![image-20210723091015891](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723091015891.png)

##### is null：

查询commission_pct字段为空的员工：

` select employee_id,last_name,commission_pct from employees where commission_pct is null;`

![image-20210723091404076](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723091404076.png)

##### 优先级：

1、算术运算符

2、连接符

3、比较符

4、is [not] null,like,[not] in

5、[not] between

6、NOT

7、and

8、or

##### order by

`select employee_id,last_name,salary from employees where department_id=80 order by salary desc;` desc为倒序，默认或asc为正序

![image-20210723092117158](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723092117158.png)

![image-20210723092151778](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723092151778.png)

先对工资排序，如果有相同的则按部门号再排序：

` select employee_id,last_name,salary,department_id from employees order by salary asc,department_id asc;`

并且可以使用别名进行排序。

##### 单行函数

lower()、upper()、initcap()（第一个字母为大写）;

`select lower('ABC'),upper('abc'),initcap('ABC abc')from dual; `

![image-20210723095253399](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723095253399.png)

查询名字转化后为king的员工信息：`select * from employees where lower(last_name) = 'king';`

![image-20210723095538819](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723095538819.png)

concat()连接函数，substr()截取函数，length()计算长度，instr()判断字符在字符串中位置，lpad()左对齐，rpad()右对齐，trim()移除，replace()指定字符替换函数。

`select concat('hello',' world'),substr('hello world',1,6),length('hello world') from dual;`

![image-20210723100336710](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723100336710.png)

` select instr('hello world','w') from dual;` 如果不存在输出0

![image-20210723100602704](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723100602704.png)

`select employee_id,lpad(salary,20,'*') from employees;`左对齐：

![image-20210723100844528](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723100844528.png)

`select employee_id,rpad(salary,20,' ') from employees;` 右对齐：

![image-20210723100919855](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723100919855.png)

`select trim('h' from 'hhhello  h wordhh') from dual;` 替换收尾不替换中间字符：

![image-20210723101236534](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723101236534.png)

`select replace('world hello world world','world','zhangsan')from dual;` 替换所有匹配值：

![image-20210723101519442](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723101519442.png)

##### 多行函数

max([columns])输出该属性列的最大值

min([columns])输出该属性列的最小值

AVG([columns])输出该属性列的平均值

count([columns])输出该属性列的个数

sum()求和

stddev()方差函数

` select avg(salary),max(salary),min(salary),sum(salary) from employees;`

![image-20210726100400293](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726100400293.png)

avg(),sum(),stddev()只能对number类型运算。max()和min()和count()任何数据类型都可用。

`select count(1),count(2),count(3),count(*) from employees;`返回的具体值跟count()中的属性列没有关系，返回的是不为空的个数值。

![image-20210726101328809](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726101328809.png)

avg() = sum()/count()

` select count(department_id),count(distinct department_id) from employees;`返回不重复的部门id个数

![image-20210726102416528](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726102416528.png)

###### 分组数据group by ：使用group by 必须有多行函数使用，使用多行函数和普通属性列结合时对属性列必须有group by

######having 如果要用多行函进行条件的话，只能用having，不能用where，说明组函数是可以嵌套的,having跟where一个意思

```sql
--求出各部门中平均工资大于六千的部门，以及其平均工资
select department_id,avg(salary) 
from employees 
group by department_id
having avg(salary) >6000
```

![image-20210726104219505](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726104219505.png)

求各个部门的平均工资：` select department_id,avg(salary) from employees group by department_id;`

![image-20210726102923290](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726102923290.png)

求各个部门各个工种的平均工资：` select department_id,job_id,avg(salary) from employees group by department_id,job_id;`

![image-20210726103402924](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726103402924.png)



##### 数字函数

round()四舍五入，trunc()截断，mod()求余

`select round(3.1414926,2),round(3.14159,3),round(3.14159,0) from dual;` 保留小数点后指定位数（默认保留零位，负数则从个位数开始算）：

![image-20210723101821284](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723101821284.png)

`select trunc(3.1414926,2),trunc(3.14159,3),trunc(3.14159,-1) from dual;` tunc直接截断，不会四舍五入：

![image-20210723102231649](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723102231649.png)

`select mod(1000,9) from dual;` 求余：

![image-20210723102535995](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723102535995.png)

日期函数：

日期的数学运算：在日期上加上或减去一个数字结果仍为日期，日期不允许做加法，无意义，两个日期相减返回日期之间相差的天数，可以用数字除以24来向日期中加上或减去天数。

months_between() 两个日期相差的月数，

add_months()向指定日期中加上若干月数，

next_day()指定日期的下一个星期相对应的日期，

last_day()本月的最后一天，

round()日期四舍五入，

trunc()日期截断。

` select sysdate,sysdate+1,sysdate-3,round(trunc(sysdate-hire_date)/30) work_date from employees;` 计算每个员工来公司多少个月了：

![image-20210723103358111](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723103358111.png)

` select employee_id,months_between(sysdate,hire_date) from employees;` 

![image-20210723104435945](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723104435945.png)

`select add_months(sysdate,4),next_day(sysdate,'星期日') from dual;` 以系统时间开始后四个月以及下个星期日的日期：

![image-20210723104715407](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723104715407.png)

`select last_day(sysdate) from dual;` 查询本月最后一天：

![image-20210723104907454](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723104907454.png)

`select last_name,hire_date from employees where hire_date=last_day(hire_date)-1;` 查询是当月倒数第二天来公司的员工：

![image-20210723105130415](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723105130415.png)

`select round(sysdate,'month'),trunc(sysdate) from dual;`  四舍五入和截断：

![image-20210723105359819](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723105359819.png)

###### 显示数据类型转换：

to_date()，to_char()，to_number()；

`select employee_id,last_name,hire_date from employees where to_char(hire_date,'yyyy-MM-dd') = '1994-06-07';`

`select employee_id,last_name,hire_date from employees where to_date('1994-06-07','yyyy-MM-dd') = hire_date;`

`select employee_id,last_name,to_char(hire_date,'yyyy"年"MM"月"dd"日"') from employees where to_char(hire_date,'yyyy"年"MM"月"dd"日"') = '1994年06月07日';`

![image-20210723110359803](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723110359803.png)

` select to_char(1234.12,'999,999,999.99'),to_char(1234.12,'000,000,000.000'),to_char(1234.12,'$999,999,999.99'),to_char(1234.12,'l999,999,999.99') from dual;` 用999时不会补空，000时会补空，前面加$为美元表示，前面有L表示本地货币表示：

![image-20210723111203089](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723111203089.png)

` select to_number('$1,234.12','$999,999,999.99')+1 from dual;`

![image-20210723111611129](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723111611129.png)

##### 通用函数

适用于任何数据类型，同时也适用于空值

NVL(expr1,expr2)

NVL2(3xpr1,expr2,expr3)

NULLIF(expr1,expr2)：相等返回null，不等返回expr1

COALESCE(expr1,expr2,...,exprn)：coalesce与nvl相比的优点在于coalesce可以同时处理交替的多个值，如果第一个表达式为空，则返回下一个表达式，对其他的参数尽心coalesce。

`select employee_id,last_name,salary*12*(1+nvl(commission_pct,0)) from employees;` 判断函数第一个值是否为空，如果为空则用第二个值代替，不为空则使用本身。

![image-20210723112329332](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723112329332.png)

`select employee_id,last_name,nvl(to_char(department_id,'9999'),'没有部门') from employees;`

![image-20210723112726384](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723112726384.png)

`select employee_id,last_name,salary*12*(1+nvl2(commission_pct,0.15,0.1)) from employees;`如果commission_pct不为空则返回0.15,为空则返回0.1:

![image-20210723113113658](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723113113658.png)

##### 条件表达式

在SQL语句中使用IF-TTHEN-ELSE逻辑

使用两种方法：

-CASE表达式

-DECODE函数

```sql
--查询部门编号为10,20,30员工信息，部门为10则工资乘1.1，部门为20则工资乘1.2，部门为30则乘1.3
select employee_id,last_name,department_id,case department_id when 10 then salary*1.1
                                                              when 20 then salary*1.2
                                                              else salary*1.3 end new_sal
from employees where department_id in (10,20,30)
```

![image-20210723114418593](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723114418593.png)

```sql
select employee_id,last_name,department_id,decode(department_id,10,salary*1.1,
                                                                20,salary*1.2,
                                                                30,salary*1.3,
                                                                salary) new_sal
from employees
where department_id in (10,20,30)
```

![image-20210723115244327](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723115244327.png)

#### 多表查询

join...on...

where（查询全部符合调条件的行）

left join/left outer join左外连接（以左边的表为参照，右边没有该属性也会输出）

right join/right outer join 右外连接（与上同理，以右边对齐方式）

full join 满外连接（两边都会全部查询，两边都对齐）

cross join（会产生笛卡尔积）

natural join（自然连接，会将两个表中的所有相同属性进行匹配连接）

######如多多表查询时没有条件，则会产生笛卡尔积查询错误，即总查询条数等于左边的表查询条数乘以右边表查询条数

`select a.employee_id,last_name,a.department_id,b.department_name from employees a join departments b on a.employee_id = b.department_id;` 查询员工表中存在于部门表的员工信息

![image-20210723171621731](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723171621731.png)

查询员工表中所有员工的部门和部门信息：` select a.employee_id,last_name,a.department_id,b.department_name from employees a,departments b where a.department_id = b.department_id;`

或：` select a.employee_id,last_name,department_id,b.department_name from employees a inner join departments b using(department_id);`

![image-20210726094500093](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726094500093.png)

右外连接 right join/right outer join:`select a.employee_id,last_name,a.department_id,b.department_name from employees a right join departments b on a.employee_id = b.department_id;`



![image-20210723172145653](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210723172145653.png)

![image-20210726093948251](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726093948251.png)

右连接：`select employee_id,last_name,department_name from employees e,departments d where e.department_id(+) = d.department_id;`

![image-20210726093729620](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726093729620.png)

##### 等值查询

`select employee_id,last_name,department_name from employees e,departments d where e.department_id = d.department_id;`

##### 非等值查询

查询员工工资等级：`select employee_id,last_name,salary,grade_level from employees e,job_grades j where e.salary between j.lowest_sal and j.highest_sal;`

![image-20210726091506450](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726091506450.png)

##### 自连接

查询员工表中‘Chen’的manager信息：

```sql
select e1.employee_id,e1.last_name,e1.manager_id,e2.employee_id,e2.last_name 
from employees e1 join employees e2 
on e1.manager_id = e2.employee_id 
and lower(e1.last_name) = 'chen'
```

![image-20210726092546167](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726092546167.png)

##### 多表查询总结

```text
SQL语句的多表查询方式：

例如：按照department_id查询employees(员工表)和departments(部门表)
的信息。
方式一(通用型):SELECT ... FROM ... WHERE
SELECT e.last_name,e.department_id,d.department_name
FROM employees e,departments d
where e.department_id = d.department_id

方式二：SELECT ... FROM ... NATURAL JOIN ...
有局限性：会自动连接两个表中相同的列(可能有多个:department_id和manager_id)
SELECT last_name,department_id,department_name
FROM employees
NATURAL JOIN departments

方式三：SELECT ... JOIN ... USING ...
有局限性：好于方式二，但若多表的连接列列名不同，此法不合适
SELECT last_name,department_id,department_name
FROM employees
JOIN departments
USING(department_id)

方式四：SELECT ... FROM ... JOIN ... ON ...
常用方式，较方式一，更易实现外联接(左、右、满)
SELECT last_name,e.department_id,department_name
FROM employees e
JOIN departments d
ON e.department_id = d.department_id


--内连接
    1）
    --等值连接
    --不等值连接
    2）
    --非自连接
    --自连接

--外连接
    --左外连接、右外连接、满外连接
```

#### 子查询 

子查询在主查询之前一次执行完成，子查询的结果被主查询使用

查询工资比Abel的工资高：`select employee_id,last_name,salary from employees where salary>(select salary from employees where highest(last_name)='Abel');`

或

```sql
select employee_id,last_name,salary from employees 
where salary>(
              select salary from employees 
              where upper(last_name)='ABEL')
```

![image-20210726105204941](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726105204941.png)

```sql
--返回job_id与141号员工相同,salary比143号员工多的员工姓名，job_id,salary
select last_name,job_id,salary from employees 
where job_id = (select job_id from employees 
                where employee_id = 141)
           and salary>(select salary from employees
                       where employee_id = 143)
```

![image-20210726110647869](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726110647869.png)

```sql
--查询最低工资大于50号部门最低工资的部门id和其最低工资
select department_id,min(salary) from employees
group by department_id
having min(salary) > (select min(salary) from employees where 
                                                        department_id = 50)
```

![image-20210726111630230](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726111630230.png)

###### 多行子查询

in:等于列表中的任意一个

any:和子查询返回的某一个值比较

all:和子查询返回的所有值比较

```sql
--返回其他部门中比job_id为'IT_PROG'部门任一工资低的员工的员工号、姓名、job_id以及salary
select employee_id,last_name,job_id,salary from employees
where salary < any(select salary from employees where 
                   job_id = 'IT_PROG')
                   and job_id<>'IT_PROG'
```

![image-20210726112543558](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726112543558.png)

```sql
--返回其他部门中比job_id为'IT_PROG'部门所有工资低的员工的员工号、姓名、job_id以及salary
select employee_id,last_name,job_id,salary from employees
where salary < all(select salary from employees where 
                   job_id = 'IT_PROG')
                   and job_id<>'IT_PROG'

```

#### 创建和管理表

##### 表名和列名命名规则：

必须以字母开头

必须在1-30个字符之间

必须只能包含A-Z,a-z,0-9,_,$和#

必须不能和用户定义的其他对象重名

必须不能是Oracle的保留字

######create table：

创建表的第一种方式（白手起家）

```sql
create table emp1(
emp1_id number(8),
emp1_name varchar2(20),
salary number(10,2),
hire_date date
)
```

![image-20210726120121710](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726120121710.png)

第二种方式（依托于现有的表，而且原来表的数据也会导入进来，如果不想要数据，只需添加一个没有符合值的条件查询语句即可，例如添加where 1 = 2）：

```sql
create table emp2
as 
select employee_id,last_name,hire_date,salary 
from employees
```

###### alter table

```sql
alter table emp1
add (email varchar2(20))
```

![image-20210726125226676](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726125226676.png)

```sql
alter table emp1
modify(emp1_id number(15))
```

![image-20210726125351576](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726125351576.png)

```sql
alter table emp1
modify(salary number(10,2) default 2000)
```

![image-20210726125533717](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726125533717.png)

修改后只对以后的数据起作用

```sql
--删除一个列
alter table emp1
drop column email
```

![image-20210726125925577](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726125925577.png)

```sql
--修改一个列名
alter table emp1
rename column salary to gongzi
```

![image-20210726130233482](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726130233482.png)

删除表：`drop table emp2;`

![image-20210726130531090](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726130531090.png)

清空表：`truncate table emp2;`

![image-20210726130751951](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726130751951.png)

更改表名：` rename emp2 to employees2;`

![image-20210726131041730](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726131041730.png)

##### 总结DDL语句

create table 创建表

alter table 修改表结构

drop table删除表

rename to 重命名表

truncate table 清空表

DDL都不可回滚

#### 数据操纵语言（DML）commit后也不可回滚

插入语句：insert into table(column[,column,...]) values(value[,value,...]);

```sql
insert into employees2
values(1001,'张三',to_date('1997-06-09','yyyy-MM-dd'),2400.23)
```

![image-20210726132249750](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726132249750.png)

或

```sql
insert into emp2 
values(&employee_id,'&last_name','&hire_date',&salary)
```



更新语句：update table_name set column_name =column;

```sql
--更新114号员工的工作和工资使其与205号员工相同
update employees
set job_id = (
           select job_id
           from employees
           where employee_id = 205),
    salary = (
           select salary
           from employees
           where employee_id = 205)
```

删除语句：delete  from table_name where ...;

