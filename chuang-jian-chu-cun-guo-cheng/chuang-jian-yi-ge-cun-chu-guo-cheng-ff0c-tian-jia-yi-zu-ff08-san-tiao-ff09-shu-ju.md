# 创建一个存储过程，添加一组数据

### 一组数据代表

* ## **一条银行卡消息数据**
* ## **一条银行网点更新数据**
* ## **一条银行卡与用户的关系数据**

## 存储过程名称

```
proc_createUserAndBankCrad
```

## 存储过程参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 存储过程返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 代码

```
/**
创建一个存储过程用来产生一个用户的银行卡
存储过程名称：proc_createUserAndBankCrad
参数：
  无
返回值：
  无
日期时间：2018年11月15日20点49分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_createUserAndBankCrad
  AS
BEGIN
  -- 这是一个事务
  BEGIN TRANSACTION
    -- 一个随机的银行卡的卡号
    DECLARE @bank_crad_number VARCHAR(20)
    -- 一个随机的用户
    DECLARE @user_id_number VARCHAR(20)
    -- 一个默认密码
    DECLARE @password VARCHAR(7)
    -- 一个币种编号
    DECLARE @type INT
    -- 一个存款类型的编号
    DECLARE @kind INT
    -- 一个随机的开户日期
    DECLARE @date VARCHAR(12)
    -- DATE 格式的日期
    DECLARE @dateDate DATE
    -- 一个随机的开户金额
    DECLARE @money INT
    DECLARE @moneyI DECIMAL (8, 4)
    --  我的余额
    DECLARE @balance INT
    DECLARE @balanceI DECIMAL (8, 4)
    --  标志是否挂失
    DECLARE @isLoss INT
    -- 你的银行卡的注册网点的标号
    DECLARE @dotNumber VARCHAR(7)
    -- 表示是否挂失
    DECLARE @overTheCrad INT
    -- 获取银行卡的卡号
    -- 获取银行网点信息编号
    EXEC proc_randBankCard @bank_crad_number OUT, @dotNumber OUT
    -- 随机取出一个用户
    EXEC proc_getRandUser @user_id_number OUT
    -- 密码
    SET @password = '888888'
    -- 币种：人民币
    SET @type = 1
    -- 存款类型
    SET @kind = 1
    -- 设置开户金额
    SET @money = 100 * CAST((RAND() * 30 + 1) AS INT)
    SET @moneyI = CAST(CAST(@money AS VARCHAR(5)) + '.00' AS DECIMAL (8, 4))
    -- 设置余额
    SET @balance = @money
    SET @balanceI = CAST(CAST(@balance AS VARCHAR(5)) + '.00' AS DECIMAL (8, 4))
    -- 没有挂失
    SET @isLoss = 0
    -- 没有注销
    SET @overTheCrad = 0
    -- 设置开户编号日期
    EXEC proc_getRandDateByUserId @user_id_number, @date OUT
    SET @dateDate = CAST(@date AS DATE)
    -- 为用户绑定一张银行卡
    EXEC proc_linkUserAndCrad @user_id_number, @bank_crad_number
    --存入数据
    INSERT INTO tb_back_number_table(bank_card_number,
                                     password,
                                     kind_of_bank_card,
                                     deposit_type,
                                     create_crad_date,
                                     account_opening_amount,
                                     account_balance,
                                     is_loss,
                                     dot_id,
                                     is_cancellation)
    VALUES (@bank_crad_number,
            @password,
            @kind,
            @kind,
            @dateDate,
            @moneyI,
            @balanceI,
            @isLoss,
            @dotNumber,
            @overTheCrad)
    IF ((SELECT bank_card_number
         FROM tb_back_number_table
         WHERE bank_card_number = @bank_crad_number)
        IS NOT NULL)
       AND
       ((SELECT table_id
         FROM tb_user_bank_information_table
         WHERE user_ID = @user_id_number
               AND
               bank_card_number = @bank_crad_number)
        IS NOT NULL)
      BEGIN
        COMMIT TRANSACTION
      END
    ELSE
      BEGIN
        print '没有添加联系，回滚事务'
        ROLLBACK TRANSACTION
      END
END
```

## 测试代码

```
-- 测试代码
DECLARE @number INT
SET @number = 1
WHILE @number < 10000
  BEGIN
    EXEC proc_createUserAndBankCrad;
    SET @number = @number + 1
  END
```



