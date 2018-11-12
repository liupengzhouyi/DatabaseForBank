# 银行客户信息表

## 表结构

| 字段名称 | 数据类型 | 是否主键 | 是否自增 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| user\_ID | VARCHAR\(20\) | 是 | 否 | 客户身份证号码 |
| user\_name | VARCHAR\(20\) | 否 | 否 | 客户名称 |
| user\_phone\_number | VARCHAR\(15\) | 否 | 否 | 客户联系方式 |
| user\_address | VARCHAR\(45\) | 否 | 否 | 客户地址 |

## 创建表的代码

```
-- 创建用户表
CREATE TABLE tb_user_table
(
  -- 用户身份证号码
  user_ID           VARCHAR(20) PRIMARY KEY,
  -- 用户姓名
  user_name         VARCHAR(20),
  -- 用户电话号码
  user_phone_number VARCHAR(15),
  -- 用户地址
  user_address      VARCHAR(45)
);
```



