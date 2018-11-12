# 银行卡账户信息表

## 表结构


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

