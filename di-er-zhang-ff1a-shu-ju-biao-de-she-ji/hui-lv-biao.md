# 汇率信息表

## 表结构

| 字段名称 | 数据类型 | 是否为主键 | 是否自增 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| table\_id | INT | 是 | 是 | 一个自增的主键 |
| currency\_A | INT | 否 | 否 | 货币A的编号 |
| currency\_B | INT | 否 | 否 | 货币B的编号 |
| exchange\_rate | DECIMAL\(5, 4\) | 否 | 否 | A对B的汇率 |

## 实现代码

```
-- 汇率信息表
CREATE TABLE tb_exchange_rate_table
(
  -- ID 主键
  table_id INT PRIMARY KEY IDENTITY (1, 1) ,
  -- 币种A的编号（人民币）
  currency_A INT NOT NULL ,
  -- 币种B的编号（美元）
  currency_B INT NOT NULL ,
  --汇率 （1 美元 = 7 人民币） 7
  exchange_rate DECIMAL(5, 4) NOT NULL
);
```



