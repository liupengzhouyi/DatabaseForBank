# 一个自动化实现随机取钱的存储过程

# 存储过程名称

```
proc_ranDateGetMoney
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 代码

```
-- 写一个随机取钱的存储过程
CREATE PROCEDURE proc_ranDateGetMoney
  AS
  BEGIN
    BEGIN TRANSACTION
    DECLARE @cradNumber VARCHAR(20)
    DECLARE @password VARCHAR(7)
    DECLARE @money DECIMAL (8, 4)
    DECLARE @moneyI DECIMAL (8, 4)
    DECLARE @moneyII DECIMAL (8, 4)
    -- 赋值
    EXEC proc_getACradNumberForTable @cradNumber OUT

    SET @money = CAST((RAND() * 3 ) + 1 AS INT) * 100
    SET @password = '888888'
    -- 获取转帐前的银行卡的金额
    EXEC proc_newMoneyInCrad @cradNumber, @moneyI OUT


    -- 随机日期取钱
    EXEC proc_withdrawal @cradNumber, @password, @money, 1

    -- 获取转帐后的银行卡的金额
    EXEC proc_newMoneyInCrad @cradNumber, @moneyII OUT
    -- 设置余额更新是否过程的锁
    DECLARE @numberI INT
    -- 设置余额核对策略编号 取钱
    DECLARE @kindI INT
    SET @kindI = 1
    EXEC proc_moneyIsRight @money, @moneyI, @moneyII, @kindI, @numberI OUT
    -- 判断事务的执行情况
    IF @numberI = 1
      BEGIN
        -- 可以提交事务了
        COMMIT TRANSACTION
      END
    ELSE
      BEGIN
        -- 发生了错误，转账信息出错
        -- 回滚事务
        PRINT '取钱失败！表面原因是：原因未知！实际原因：金额核对不正确！'
        ROLLBACK TRANSACTION
      END
  END
```

## 测试代码

```
-- 测试 代码
EXEC proc_ranDateGetMoney;
```



