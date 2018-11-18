# 一个自动化实现转账的存储过程

# 存储过程名称

```
proc_randDateToWithdrawal
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
-- 创建一个事务，实现一次转账
CREATE PROCEDURE proc_randDateToWithdrawal
  AS
  BEGIN
    BEGIN TRANSACTION
    DECLARE @cradNumberI VARCHAR(20)
    DECLARE @cradNumberII VARCHAR(20)
    DECLARE @password VARCHAR(7)
    DECLARE @money DECIMAL (8, 4)
    DECLARE @moneyAI DECIMAL (8, 4)
    DECLARE @moneyAII DECIMAL (8, 4)
    DECLARE @moneyBI DECIMAL (8, 4)
    DECLARE @moneyBII DECIMAL (8, 4)
    -- 赋值
    EXEC proc_getACradNumberForTable @cradNumberI OUT
    EXEC proc_getACradNumberForTable @cradNumberII OUT
    SET @money = CAST((RAND() * 3 ) + 1 AS INT) * 100
    SET @password = '888888'
    -- 获取转帐前的银行卡的金额
    EXEC proc_newMoneyInCrad @cradNumberI, @moneyAI OUT
    EXEC proc_newMoneyInCrad @cradNumberII, @moneyBI OUT
    -- 随机日期转账
    EXEC proc_saveMoneyToOtherCrad @cradNumberI, @password, @cradNumberII, @money, 0
    -- 获取转帐后的银行卡的金额
    EXEC proc_newMoneyInCrad @cradNumberI, @moneyAII OUT
    EXEC proc_newMoneyInCrad @cradNumberII, @moneyBII OUT
    DECLARE @numberI INT
    DECLARE @numberII INT
    DECLARE @kindI INT
    DECLARE @kindII INT
    SET @kindI = 1
    SET @kindII = 0
    EXEC proc_moneyIsRight @money, @moneyAI, @moneyAII, @kindI, @numberI OUT
    EXEC proc_moneyIsRight @money, @moneyBI, @moneyBII, @kindII, @numberII OUT
    -- 判断事务的执行情况
    IF @numberI = 1 AND @numberII = 1
      BEGIN
        -- 没有错误
        IF @cradNumberI = @cradNumberII
          BEGIN
            -- 发生了错误，转账信息出错
            -- 回滚事务
            PRINT '转账的卡号不可以相同'
            ROLLBACK TRANSACTION
          END
        ELSE
          BEGIN
            -- 可以提交事务了
            COMMIT TRANSACTION
          END
      END
    ELSE
      BEGIN
        -- 发生了错误，转账信息出错
        -- 回滚事务
        PRINT '转账失败！表面原因是：原因未知！实际原因：金额核对不正确！'
        ROLLBACK TRANSACTION
      END
  END
```

## 测试代码

```
-- 测试代码
EXEC proc_randDateToWithdrawal;
```



