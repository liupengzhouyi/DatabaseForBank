# 如何批量生成大量的客户信息代码

## 思路

* ### **需要用户姓名**
* 一个姓氏表和一个名称表

* 每一次取出一个姓氏取出一个名称
* 组合在一起

* ### **需要一个生成身份证号码的工具**
* 前6位

* 中间的生日
* 后三位的随机码
* 最后一位的校验码

* ### **要去重**
* select语句找到重复，重新执行

* 如果没有找到，插入数据到数据表

## 代码

```
-- 创建一个储存过程
begin transaction
-- 开始时间
DECLARE @BeginDdate DATE
-- 结束时间
DECLARE @endDdate DATE
-- 姓氏
DECLARE @frist_name VARCHAR(10)
-- 名字
DECLARE @last_name VARCHAR(10)
-- 姓名
DECLARE @name VARCHAR(20)
-- 电话号码
DECLARE @phoneNumber VARCHAR(15)
-- 设置身份证号码
DECLARE @id VARCHAR(20)
-- 身份证号码前 6 位
DECLARE @id_0_6 VARCHAR(7)
-- 身份证号码前 7-15 位
-- 随机年
DECLARE @year INT
-- 随机月
DECLARE @month INT
-- 随机日
DECLARE @day INT
-- 随机年
DECLARE @char_year VARCHAR(4)
-- 随机月
DECLARE @char_month VARCHAR(2)
-- 随机日
DECLARE @char_day VARCHAR(2)
DECLARE @id_7_15 VARCHAR(9)
-- 三位随机数
DECLARE @id_16_18 VARCHAR(4)
-- 校验码
DECLARE @last_number INT
-- 地址
DECLARE @address VARCHAR(45)
-- 地址的主键
DECLARE @main_address INT
--计数器
DECLARE @count INT
-- 设置开始时间
SET @BeginDdate = GETDATE()
-- 初始化计数器
SET @count = 1
WHILE @count < 200000
  BEGIN
    -- 获取姓氏
    SET @frist_name = (SELECT TOP 1 surname FROM tb_temp_surname_table ORDER BY NEWID())
    -- 获取名字
    SET @last_name = (SELECT TOP 1 name FROM tb_temp_name_table ORDER BY NEWID())
    -- 生成姓名
    SET @name = @frist_name + @last_name
    -- 随机生成的电话号码
    SET @phoneNumber = CONVERT(VARCHAR, CAST(RAND()* (139 - 130) + 130 AS INT)) + CONVERT(VARCHAR, CAST(RAND() * (99999999 - 32928404) + 32928404 AS int))
    IF (@phoneNumber = (SELECT user_phone_number FROM tb_user_table where user_phone_number = @phoneNumber))
      BEGIN
        CONTINUE;
      END
    -- 设置身份证号码的前6位
    SET @main_address = (SELECT TOP 1 number FROM tb_temp_address_table ORDER BY NEWID())
    SET @id_0_6 = (SELECT address_number FROM tb_temp_address_table WHERE number = @main_address)
    SET @address = (SELECT address_name FROM tb_temp_address_table WHERE number = @main_address)
    -- 设置身份证号码的前7-15位
    SET @year = CONVERT(varchar, CAST(RAND()* (40) + 1960 AS int))
    SET @char_year = CAST (@year AS VARCHAR(4))
    SET @month = CONVERT(varchar, CAST(RAND()* (11) + 1 AS int))
    SET @day = CONVERT(varchar, CAST(RAND()* (27) + 1 AS int))
    IF (@day < 10)
      BEGIN
        SET @char_day = '0' + CAST(@day AS VARCHAR(1))
      end
    ELSE
      begin
        SET @char_day = CAST(@day AS VARCHAR(2))
      end
    IF (@month < 10)
      BEGIN
        SET @char_month = '0' + CAST(@month AS VARCHAR(1))
      end
    ELSE
      BEGIN
        SET @char_month = CAST(@month AS VARCHAR(2))
      end
    SET @id_7_15 = @char_year + @char_month + @char_day
    -- 设置身份证号码的前3位
    SET @id_16_18 = CAST((RAND() * (888) + 110) AS INT)
    -- 设置身份证号码校验码
    SET @id = @id_0_6 + @id_7_15 + @id_16_18
    -- SELECT @id as 'id'
    SET @last_number = (SUBSTRING(@id,1,1)*7+
                        SUBSTRING(@id,2,1)*9+
                        SUBSTRING(@id,3,1)*10+
                        SUBSTRING(@id,4,1)*5+
                        SUBSTRING(@id,5,1)*8+
                        SUBSTRING(@id,6,1)*4+
                        SUBSTRING(@id,7,1)*2+
                        SUBSTRING(@id,8,1)*1+
                        SUBSTRING(@id,9,1)*6+
                        SUBSTRING(@id,10,1)*3+
                        SUBSTRING(@id,11,1)*7+
                        SUBSTRING(@id,12,1)*9+
                        SUBSTRING(@id,13,1)*10+
                        SUBSTRING(@id,14,1)*5+
                        SUBSTRING(@id,15,1)*8+
                        SUBSTRING(@id,16,1)*4+
                        SUBSTRING(@id,17,1)*2)%11
    IF (@last_number = 0)
      BEGIN
        SET @id  = @id + '1'
      END
    ELSE IF (@last_number = 1)
      BEGIN
        SET @id  = @id + '0'
      END
    ELSE IF (@last_number = 2)
      BEGIN
        SET @id  = @id + 'X'
      END
    ELSE IF (@last_number = 3)
      BEGIN
        SET @id  = @id + '9'
      END
    ELSE IF (@last_number = 4)
      BEGIN
        SET @id  = @id + '8'
      END
    ELSE IF (@last_number = 5)
      BEGIN
        SET @id  = @id + '7'
      END
    ELSE IF (@last_number = 6)
      BEGIN
        SET @id  = @id + '6'
      END
    ELSE IF (@last_number = 7)
      BEGIN
        SET @id  = @id + '5'
      END
    ELSE IF (@last_number = 8)
      BEGIN
        SET @id  = @id + '4'
      END
    ELSE IF (@last_number = 9)
      BEGIN
        SET @id  = @id + '3'
      END
    ELSE IF (@last_number = 10)
      BEGIN
        SET @id  = @id + '2'
      END

    -- 去重
    IF (@id = (SELECT user_ID FROM tb_user_table where user_ID = @id))
      BEGIN
        continue ;
      END
    -- 储存用户数据
    INSERT INTO tb_user_table(user_ID, user_name, user_phone_number, user_address) VALUES (@id, @name, @phoneNumber, @address)
    SET @count = @count + 1
  END
if @@ERROR=0
  commit transaction
else
  rollback transaction
SET @endDdate = GETDATE()
print '执行时间是：' + str(DateDiff(millisecond, @endDdate, @BeginDdate)) + '毫秒';

```



