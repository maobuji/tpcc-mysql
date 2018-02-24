初始化以后查看各表的数据量
====

* 查看一下各表导入的数据量<br>
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

表数据量与初始化仓库数量的关系

列名| 一个仓库 | 2个仓库 | 6个仓库
------------ | --------------- | ------------ | ------------ 
customer | 30000 | 60000 | 180000
district | 10 | 20 | 60
history | 30000 | 60000 | 180000
item | 100000 | 100000 | 100000
new_orders | 9000 | 18000 | 54000
order_line | 299976 | 598908 | 1799838
orders | 30000 | 60000 | 180000
stock | 100000 | 200000 | 600000
warehouse | 1 | 2 | 6
合计 | 598987 | 1096930 | 3093904
------------ | --------------- | ------------ | ------------ 
customer | 30000 | 60000 | 180000
district | 10 | 20 | 60
history | 30000 | 60000 | 180000
item | 100000 | 100000 | 100000
new_orders | 9000 | 18000 | 54000
order_line | 299976 | 598908 | 1799838
orders | 30000 | 60000 | 180000
stock | 100000 | 200000 | 600000
warehouse | 1 | 2 | 6
合计 | 598987 | 1096930 | 3093904
