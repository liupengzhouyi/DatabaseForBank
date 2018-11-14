# 一个产生随机产生电话号码的存储过程

## 名称

```
proc_randPhoneNumber
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @phoneNumber | VARCHAR\(15\) | 一个电话号码 |

## 代码

```
/**
创建一个产生随机的电话号码存储过程
存储过程名称：proc_randPhoneNumber
  无。
返回值：
  1. @phoneNumber
日期时间：2018年11月14日21点31分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_randPhoneNumber
  @phoneNumber VARCHAR(15) OUTPUT
  AS
BEGIN
  DECLARE @key INT
  SET @key = 1
  -- 当产生一个全新的电话号码时
  WHILE (@key != 0)
    BEGIN
      SET @phoneNumber = CONVERT(varchar, CAST(RAND()* (139 - 130) + 130 AS int))
                     + CONVERT(varchar, CAST(RAND() * (99999999 - 32928404) + 32928404 AS int))
      EXEC proc_hasThisPhoneNumber @phoneNumber, @key OUT
    END
END
SELECT @phoneNumber;
```

## 测试代码

```
-- 运行的测试用例
DECLARE @phoneNumber VARCHAR(15);
EXEC proc_randPhoneNumber @phoneNumber;
```



