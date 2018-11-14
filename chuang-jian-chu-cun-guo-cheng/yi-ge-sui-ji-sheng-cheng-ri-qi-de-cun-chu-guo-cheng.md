# 一个随产生日期的存储过程

## 名称

```
proc_randDate
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
/**
创建产生随机日期的存储过程
存储过程名称：proc_randDate
参数：
  @yearI INT ,
  @monthI INT ,
  @yearII INT ,
  @monthII INT ,
返回值：
  @date VARCHAR(9)
日期时间：2018年11月14日22点20分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_randDate
  @yearI INT ,
  @monthI INT ,
  @yearII INT ,
  @monthII INT ,
  @date VARCHAR(9) OUTPUT
  AS
  BEGIN
    DECLARE @newYear INT
    DECLARE @newMonth INT
    DECLARE @newDay INT
    DECLARE @newCharYear VARCHAR(4)
    DECLARE @newCharMonth VARCHAR(2)
    DECLARE @newCharDay VARCHAR(2)
    SET @newYear = CAST(RAND()* (@yearII - @yearI) + @yearI AS INT)
    IF @newYear = @yearII
      BEGIN
        SET @newMonth = CAST(RAND()* (@monthII - 1) + 1 AS INT)
      END
    ELSE
      BEGIN
        SET @newMonth = CAST(RAND()* (11) + 1 AS INT)
      END
    SET @newDay = CAST(RAND()* (27) + 1 AS INT)
    SET @newCharYear = CONVERT(varchar, @newYear)
    IF @newMonth < 10
      BEGIN
        SET @newCharMonth = '0' + CONVERT(varchar, @newMonth)
      END
    ELSE
      BEGIN
        SET @newCharMonth = CONVERT(varchar, @newMonth)
      END
    IF @newDay < 10
      BEGIN
        SET @newCharDay = '0' + CONVERT(varchar, @newDay)
      END
    ELSE
      BEGIN
        SET @newCharDay = CONVERT(varchar, @newDay)
      END
    SET @date = @newCharYear + @newCharMonth + @newCharDay
  END
  SELECT @date
```



