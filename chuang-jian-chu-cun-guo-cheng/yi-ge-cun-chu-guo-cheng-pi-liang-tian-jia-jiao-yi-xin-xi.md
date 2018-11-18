# 一个存储过程批量添加交易信息

# 存储过程名称

```
proc_addDealInformation
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @count | INT | 一个计数器，要产生多少条交易信息 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 代码

```
-- 一个存储过程铺量添加交易数据
CREATE PROCEDURE proc_addDealInformation
  -- 你要多少条数据
  @count INT
  AS
  BEGIN
    DECLARE @begin datetime
    DECLARE @end datetime
    SET @begin = getdate()
    DECLARE @kind INT
    DECLARE @temp INT
    SET @temp = 1
    WHILE @temp <= @count
      BEGIN
        SET @kind = CAST(RAND() * 3 AS INT) + 1
        IF @kind = 1
          BEGIN
            EXEC proc_randDateToWithdrawal
          END
        ELSE IF @kind = 2
          BEGIN
            EXEC proc_ranDateSaveMoney
          END
        ELSE IF @kind = 3
          BEGIN
            EXEC proc_ranDateGetMoney
          END
        SET @temp = @temp + 1
      END
    SET @end = getdate()
    PRINT '执行时间：' + CAST(DATEDIFF(millisecond, @begin, @end)/1000.0 AS VARCHAR(20))
  END
```

## 测试代码

```

```



