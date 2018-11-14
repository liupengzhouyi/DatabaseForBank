# 判断一张银行卡的卡号是否已经存在

## 名称

```
proc_hasCradNumber
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @cradNumber | VARCHAR\(20\) | 一个银行卡的卡号 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @returnValue | INT | 0或者1 |

## 代码

```
/**
创建一个存储过程，判断一张银行卡是否存在
存储过程名称：proc_hasCradNumber
参数：
  @cradNumber VARCHAR(20)
返回值：
  @returnValue INT
日期时间：2018年11月14日23点26分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_hasCradNumber
  @cradNumber VARCHAR(20) ,
  @returnValue INT OUTPUT
  AS
  BEGIN
    IF (SELECT bank_card_number FROM tb_back_number_table WHERE bank_card_number = @cradNumber) IS NOT NULL
      BEGIN
        SET @returnValue = 0
      END
    ELSE
      BEGIN
        SET @returnValue = 1
      END
  END
  SELECT @returnValue
```

## 测试代码

```
-- 测试代码
DECLARE @cradNumber VARCHAR(20)
DECLARE @value INT
SET @cradNumber = ''
EXEC proc_hasCradNumber @cradNumber, @value
```



