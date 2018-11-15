# 一个存储过程判断某张银行卡是否可以使用

# 存储过程名称

```
proc_thisCradCanUse
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @cradNumber | VARCHAR\(20\) | 一个银行卡卡号 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @returnValue | INT | 一个数字 |

## 返回值说明

| 返回值 | 含义 |
| :--- | :--- |
| 0 | 这张卡片不存在 |
| 1 | 这张卡片可以干 |
| 2 | 这张卡片已经注销 |
| 3 | 这张卡片挂失 |

## 代码

```
/**
创建一个存储过程判断某张银行卡是否可以使用
存储过程名称：proc_thisCradCanUse
参数：
  @cradNumber VARCHAR(20)
返回值：
  @returnValue INT
日期时间：2018年11月15日21点53分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_thisCradCanUse
  @cradNumber VARCHAR(20) ,
  @returnValue INT OUTPUT
  AS
BEGIN
  -- 判断是否有该卡片
  IF (SELECT bank_card_number FROM tb_back_number_table WHERE bank_card_number = @cradNumber) IS NOT NULL
    -- 有
    BEGIN
      -- 判断这张卡片是否注销
      IF (SELECT bank_card_number FROM tb_back_number_table WHERE bank_card_number = @cradNumber AND is_cancellation = 0) IS NOT NULL
        -- 没有注销
        BEGIN
          -- 判断该卡片是否挂失
          IF (SELECT bank_card_number FROM tb_back_number_table WHERE bank_card_number = @cradNumber AND is_loss = 0) IS NOT NULL
            BEGIN
              -- 没有挂失
              SET @returnValue = 1
              -- 1 代表这张卡片可以干！
            END
          ELSE
            BEGIN
              SET @returnValue = 3
              -- 3 代表这张卡片挂失了
            END
        END
      ELSE
        BEGIN
          SET @returnValue = 2
          -- 2 代表这张卡片已经注销
        END
    END
  ELSE
    BEGIN
      SET @returnValue = 0;
      -- 0 代表这张卡片不存在
    END
END
SELECT @returnValue;
```

## 测试代码

```
-- 测试代码
DECLARE @cradNumber VARCHAR(20)
DECLARE @number INT
SET @cradNumber = '6228480111010000004'
EXEC proc_thisCradCanUse @cradNumber, @number
```



