# 一个自动化实现转账的存储过程

# 存储过程名称

```
proc_saveMoneyToOtherCrad
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
|  |  |  |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
|  |  |  |

## 代码

```
-- 创建一个存储过程
-- 转账
CREATE PROCEDURE proc_saveMoneyToOtherCrad
  @cradNumberI VARCHAR(20) ,
  @password VARCHAR(7) ,
  @cradNumberII VARCHAR(20) ,
  @money DECIMAL (8, 4) ,
  -- 如何操作
  -- 1 --> 今日操作
  -- 0 --> 随机日期操作
  @kindII INT
  AS
  BEGIN
    DECLARE @cradIKey INT
    DECLARE @cradIIKey INT
    DECLARE @password_key INT
    DECLARE @money_key INT
    -- 判断是否有这俩张卡片
    EXEC proc_thisCradCanUse @cradNumberI, @cradIkey OUT
    IF @cradIkey = 1
      BEGIN

        -- 验证第二张卡片
        EXEC proc_thisCradCanUse @cradNumberII, @cradIIkey OUT
        IF @cradIIkey = 1
          BEGIN
            -- 该卡片可以使用
            -- 校验密码
            EXEC proc_passwordIsRight @cradNumberI, @password, @password_key OUT
            IF @password_key = 1
              BEGIN
                -- 可以使用
                -- 查看是否有足够的钱 被取出来
                EXEC proc_canWithdrawal @cradNumberI, @money, @money_key OUT
                IF @money_key = 1
                  BEGIN
                    -- 有足够的钱可以取出来
                    -- 添加交易信息
                    IF @kindII = 1
                      BEGIN
                        EXEC proc_insertTransferInformation @cradNumberI, @cradNumberII, @money, 2
                      END
                    ELSE
                      BEGIN
                        EXEC proc_insertTransferInformation @cradNumberI, @cradNumberII, @money, 1
                      END
                    -- 更新余额信息
                    EXEC proc_trueWithdrawal @cradNumberI, @money
                    EXEC proc_trueSaveMoney @cradNumberII, @money
                  END
                ELSE
                  BEGIN
                    PRINT '您的银行卡没有足够的钱可以取出'
                  END
              END
            ELSE
              BEGIN
                PRINT '您的密码输入错误！'
              END
          END
        ELSE IF @cradIIkey = 2
          BEGIN
            PRINT '您要转入的银行卡账号已经注销'
          END
        ELSE IF @cradIIkey = 3
          BEGIN
            PRINT '您要转入的这张银行卡已经挂失'
          END
        ELSE IF @cradIIkey = 0
          BEGIN
            PRINT '您要转入的银行卡不存在'
          END
      END
    ELSE IF @cradIkey = 2
      BEGIN
        PRINT '您的该银行卡账号已经注销'
      END
    ELSE IF @cradIkey = 3
      BEGIN
        PRINT '您的这张卡片已经挂失'
      END
    ELSE IF @cradIkey = 0
      BEGIN
        PRINT '您的这张银行卡不存在'
      END
  END
```

## 测试代码

```

```



