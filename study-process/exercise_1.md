# Exercise 01

## 1.2
问题：选择products表中名称和价格
当选择多列时可以使用逗号分隔
```sql
select name, price from products
```

## 1.3
问题：选择products表中价格小于等于200的名称
当需要比较数值可以使用大于小于（>, >=, <, <=）
```sql
select name from products where price <= 200
```

## 1.5
问题：选择products表中name和price，但是price必须是美分（即price需要乘100）统计

解析：price * 100即可，也可以使用concat进行字符串连接再或者使用as进行重命名
```sql
select name, price*100 as cents from products
select name, concat(price * 100, '/cents') from products
```

## 1.6
问题：计算所有产品的平均价格

解析：利用avg函数进行计算，或者sum和count函数进行计算
```sql
select avg(price) from products
select sum(price)/count(price) from products
```

## 1.9
问题：查询价格大于180的产品，并且先根据价格降序，再根据名称升序

解析：先利用`>=`进行查询大于180的产品，再利用order by 进行排序，并且用逗号分隔排序条件
```sql
select name, price from products where price >= 180 order by price desc, name asc
```

## 1.10
问题：查询所有商品信息，同时根据products表中manufacturer字段进行匹配

解析：利用join进行匹配
```sql
-- join 语法 --
SELECT column1, column2, ...
FROM table1
JOIN table2 ON condition;
```
解答：
```sql
select products.*, manufacturers.`Name` as 'manufacturers name' from products JOIN manufacturers on (products.Manufacturer=manufacturers.`Code`)
```
## 1.11
问题：查询所有商品信息的名称和价格信息以及制造商名称

解答：
```sql
select products.name, products.Price, manufacturers.`Name` as 'manufacturers name' from products JOIN manufacturers on (products.Manufacturer=manufacturers.`Code`)
```

