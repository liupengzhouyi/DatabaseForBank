# 汇率信息表

## 表结构


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

