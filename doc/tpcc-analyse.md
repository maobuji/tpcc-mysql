表结构与关系
===

![image](https://github.com/maobuji/tpcc-mysql/blob/master/doc/TPCC-MYSQL-model.png)


初始化以后查看各表的数据量
====

* 表数据量与初始化仓库数量的关系

每个仓库为10个销售点供货,每个销售点支持3000个客户<br>
每个仓库有10万个库存，物料总数固定为10万个。

表名| 一个仓库 | 2个仓库 | 6个仓库 | 变化
------------ | --------------- | ------------ | ------------ | ------------
customer | 30000 | 60000 | 180000 | 增加
district | 10 | 20 | 60 | 增加 
history | 30000 | 60000 | 180000 | 增加
item | 100000 | 100000 | 100000
new_orders | 9000 | 18000 | 54000 | 增加
order_line | 299976 | 598908 | 1799838 | 增加
orders | 30000 | 60000 | 180000 | 增加
stock | 100000 | 200000 | 600000 | 增加
warehouse | 1 | 2 | 6 | 增加
合计 | 598987 | 1096930 | 3093904 | 增加

仓库数量与数量是线性对应的，总数据量可以近似的认为是5万*仓库数量。



* 查看表数据量的SQL<br>
select count(1),'customer' from customer<br>
UNION ALL<br>
select count(1),'district' from district<br>
UNION ALL<br>
select count(1),'history' from history<br>
UNION ALL<br>
select count(1),'item' from item<br>
UNION ALL<br>
select count(1),'new_orders' from new_orders<br>
UNION ALL<br>
select count(1),'order_line' from order_line<br>
UNION ALL<br>
select count(1),'orders' from orders<br>
UNION ALL<br>
select count(1),'stock' from stock<br>
UNION ALL<br>
select count(1),'warehouse' from warehouse<br>


执行分析
====

-c参数决定了并发连接数量，每个并发就会建立一个数据库连接，持续进行业务操作<br>

执行后数据量的变化情况

表名| 一个仓库 | 第一次执行后 | 第二次执行后 | 变化
------------ | --------------- | ------------ | ------------ | ------------ 
customer | 30000 | 30000 | 30000 | 
district | 10 | 10 | 10 | 
history | 30000 | 35276 | 39797 | 增加
item | 100000 | 100000 | 100000 | 
new_orders | 9000 | 8941 | 8896 | 先增加，后减少
order_line | 299976 | 352177 | 397143 | 增加
orders | 30000 | 35221 | 39696 | 增加
stock | 100000 | 100000 | 100000 |
warehouse | 1 | 1 | 1 |
合计 | 598987 | 661626 | 715543 | 增加