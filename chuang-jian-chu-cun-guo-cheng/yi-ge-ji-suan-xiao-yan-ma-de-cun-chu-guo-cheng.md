# 一个存储过程计算身份证的校验吗

## 名称

```
proc_checkCodeInIdCard
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @idNumber\_17 | VARCHAR\(20\) | 身份证的前17 位 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @idNumber\_18 | VARCHAR\(20\) | 一个完整的身份证 |

## 代码

```
/**
创建一个存储过程计算身份证的校验吗
存储过程名称：proc_checkCodeInIdCard
参数：
  @idNumber_17 VARCHAR(20)
返回值：
  @idNUmber_18 VARCHAR(20)
日期时间：2018年11月15日12点37分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_checkCodeInIdCard
  @idNumber_17 VARCHAR(20) ,
  @idNUmber_18 VARCHAR(20) OUTPUT
  AS
  BEGIN
    DECLARE @last_number INT
    SET @last_number = (SUBSTRING(@idNumber_17,1,1)*7+
                          SUBSTRING(@idNumber_17,2,1)*9+
                          SUBSTRING(@idNumber_17,3,1)*10+
                          SUBSTRING(@idNumber_17,4,1)*5+
                          SUBSTRING(@idNumber_17,5,1)*8+
                          SUBSTRING(@idNumber_17,6,1)*4+
                          SUBSTRING(@idNumber_17,7,1)*2+
                          SUBSTRING(@idNumber_17,8,1)*1+
                          SUBSTRING(@idNumber_17,9,1)*6+
                          SUBSTRING(@idNumber_17,10,1)*3+
                          SUBSTRING(@idNumber_17,11,1)*7+
                          SUBSTRING(@idNumber_17,12,1)*9+
                          SUBSTRING(@idNumber_17,13,1)*10+
                          SUBSTRING(@idNumber_17,14,1)*5+
                          SUBSTRING(@idNumber_17,15,1)*8+
                          SUBSTRING(@idNumber_17,16,1)*4+
                          SUBSTRING(@idNumber_17,17,1)*2)%11
      IF (@last_number = 0)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '1'
        END
      ELSE IF (@last_number = 1)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '0'
        END
      ELSE IF (@last_number = 2)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + 'X'
        END
      ELSE IF (@last_number = 3)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '9'
        END
      ELSE IF (@last_number = 4)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '8'
        END
      ELSE IF (@last_number = 5)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '7'
        END
      ELSE IF (@last_number = 6)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '6'
        END
      ELSE IF (@last_number = 7)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '5'
        END
      ELSE IF (@last_number = 8)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '4'
        END
      ELSE IF (@last_number = 9)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '3'
        END
      ELSE IF (@last_number = 10)
        BEGIN
          SET @idNumber_18  = @idNumber_17 + '2'
        END
  END
  SELECT @idNUmber_18
```

## 测试代码

```
-- 测试代码
DECLARE @id_numberI VARCHAR(20)
DECLARE @id_numberII VARCHAR(20)
SET @id_numberI = '15263119971007091'
EXEC proc_checkCodeInIdCard @id_numberI, @id_numberII;
```



