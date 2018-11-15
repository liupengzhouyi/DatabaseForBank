# 存储过程名称

```
proc_getRandDateByUserId
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @userId | VARCHAR\(20\) | 一个身份证号码 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @date | VARCHAR\(15\) | 一个日期 |

## 代码

```
-- 创建一个存储过程
  -- 通过你的身份证号码，获取一个大于你18岁的日期
/**
创建一个存储过程通过你的身份证号码，获取一个大于你18岁的日期
存储过程名称：proc_getRandDateByUserId
参数：
  @userId VARCHAR(20)
返回值：
  @date VARCHAR(15)
日期时间：2018年11月15日16点44分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_getRandDateByUserId
  @userId VARCHAR(20) ,
  @date VARCHAR(15) OUTPUT
  AS
  BEGIN
    DECLARE @year INT
    DECLARE @month INT
    DECLARE @day INT
    DECLARE @varcharYear VARCHAR(4)
    DECLARE @varcharMonth VARCHAR(2)
    DECLARE @varcharDay VARCHAR(2)

    SET @year = SUBSTRING(@userId,7,1)*1000+
               SUBSTRING(@userId,8,1)*100+
               SUBSTRING(@userId,9,1)*10+
               SUBSTRING(@userId,10,1)*1 + 18;
    SET @month = SUBSTRING(@userId,11,1)*10+
                SUBSTRING(@userId,12,1)*1;
    SET @day = SUBSTRING(@userId,13,1)*10+
              SUBSTRING(@userId,14,1)*1;
    SET @varcharYear = (CAST(@year AS VARCHAR(4)))
    EXEC proc_cradTypeToVarchar @month, @varcharMonth OUT
    EXEC proc_cradTypeToVarchar @day, @varcharDay OUT
    SET @date = @varcharYear + '-' + @varcharMonth + '-' + @varcharDay
  END
  SELECT @date
```

## 测试代码

```
-- 测试代码
DECLARE @user_id VARCHAR(20)
DECLARE @date VARCHAR(20)
SET @user_id = '152631199710070912'
EXEC proc_getRandDateByUserId @user_id, @date;

```



