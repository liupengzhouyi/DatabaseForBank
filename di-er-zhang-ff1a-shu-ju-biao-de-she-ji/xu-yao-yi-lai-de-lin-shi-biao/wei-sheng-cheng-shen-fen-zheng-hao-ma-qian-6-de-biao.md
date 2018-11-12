# 身份证号码前6位信息表

## 数据表信息

| 字段名称 | 数据类型 | 是否主键 | 是否自增 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| number | int | 是 | 是 | 编号 |
| address\_number | varchar\(7\) | 否 | 否 | 前6位编号 |
| address\_name | VARCHAR\(20\) | 否 | 否 | 编号所代表的地址 |

## 创建数据表的代码

```
-- 创建一个地址表
CREATE TABLE tb_temp_address_table
(
  -- 编号
  number INT PRIMARY KEY IDENTITY (1, 1) ,
  -- 地址编号
  address_number VARCHAR(7) NOT NULL ,
  -- 地址名称
  address_name VARCHAR(20) NOT NULL
);
```



