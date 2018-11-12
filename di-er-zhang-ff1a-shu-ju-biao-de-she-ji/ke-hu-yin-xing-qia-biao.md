# 银行卡账户信息表

## 表结构

| 字段名称 | 数据类型 | 是否主键 | 是否自增 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| bank\_card\_number | VARCHAR\(20\) | 是 | 否 | 银行卡卡号 |
| password |  | 否 | 否 | 密码 |
| kind\_of\_bank\_crad |  | 否 | 否 | 银行卡种类 |
| deposit\_type |  | 否 | 否 | 存款类型 |
| create\_crad\_number |  | 否 | 否 | 开户日期 |
| account\_opening\_amount |  | 否 | 否 | 开户金额 |
| account\_balance |  | 否 | 否 | 账户余额 |
| is\_loss |  | 否 | 否 | 是否挂失 |
| dot\_id |  | 否 | 否 | 网点编号 |
| is\_cancellation |  | 否 | 否 | 是否注册 |

## 实现代码

```
--创建银行卡数据表
CREATE TABLE tb_back_number_table
(
  -- 主键， 银行卡卡号
  bank_card_number VARCHAR(20) PRIMARY KEY ,
  -- 密码
  password VARCHAR(7) NOT NULL ,
  -- 银行卡种类
  kind_of_bank_card INT ,
  -- 存款类型
  deposit_type INT ,
  -- 开户日期
  create_crad_number DATE ,
  -- 开户金额
  account_opening_amount DECIMAL (8, 4) ,
  -- 为什么不使用MONEY , 因为他不比Decimal灵活，范围大
  -- 账户余额
  account_balance DECIMAL (8, 4) ,
  -- 是否挂失
  is_loss INT NOT NULL ,
  -- 网点编号
  dot_id VARCHAR(5) NOT NULL ,
  -- 是否注销
  is_cancellation INT NOT NULL
);
```



