# 将数字转化为VARCHAR（5）的存储过程

# 存储过程名称

```
proc_countToVarchar
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @count | INT | 计数数字 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @varcharCount\(6\) | VARCHAR\(6\) | varchar类型的数字 |

## 代码

```
/**
将数字转化为varchar(5)类型的数据
存储过程名称：proc_countToVarchar
参数：
  @counnt INT
返回值：
  @varcharCount VARCHAR(2)
日期时间：2018年11月14日15点17分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_countToVarchar
  @count INT ,
  @varcharCount VARCHAR(6) OUTPUT
  AS
  BEGIN
    IF (@count < 10)
    BEGIN
      SET @varcharCount = '0000' + CAST(@count AS VARCHAR(1))
    END
  ELSE IF (@count < 100 AND @count > 9)
    BEGIN
      SET @varcharCount = '000' + CAST(@count AS VARCHAR(2))
    END
  ELSE IF (@count < 1000 AND @count > 99)
    BEGIN
      SET @varcharCount = '00' + CAST(@count AS VARCHAR(3))
    END
  ELSE IF (@count < 10000 AND @count > 999)
    BEGIN
      SET @varcharCount = '0' + CAST(@count AS VARCHAR(4))
    END
  ELSE
    BEGIN
      SET @varcharCount = CAST(@count AS VARCHAR(5))
    END
  END
  SELECT @varcharCount
```

## 测试代码

```
-- 测试代码
DECLARE @count INT
SET @count = 1
DECLARE @varcharType VARCHAR(7)
EXEC proc_countToVarchar @count, @varcharType
```



