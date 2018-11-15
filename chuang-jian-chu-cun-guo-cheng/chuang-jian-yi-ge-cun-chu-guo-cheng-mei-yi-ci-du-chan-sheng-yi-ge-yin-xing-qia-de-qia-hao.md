# 创建一个存储过程每一次都产生一个银行卡的卡号

# 存储过程名称

```
proc_createCradNumber
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @bank\_crad\_type | INT | 卡片种类 |
| @bank\_dot\_number | VARCHAR\(6\) | 卡片网点信息编号 |
| @bank\_dot\_count | INT | 计数 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @bank\_crad\_number | VARCHAR\(20\) | 一个银行卡的编号 |

## 代码

```
/**
创建每一次都产生一个银行卡的卡号
存储过程名称：proc_createCradNumber
参数：
  @bank_crad_type INT
  @bank_dot_number VARCHAR
  @bank_dot_count
返回值：
  @bank_crad_number VARCHAR(20)
日期时间：2018年11月14日23点11分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_createCradNumber
  -- 银行卡种类
  @bank_crad_type INT ,
  -- 银行网点信息
  @bank_dot_number VARCHAR(6) ,
  -- 添加的网点的事情用户的数量
  @bank_dot_count INT ,
  -- 生产的银行卡的卡号
  @bank_crad_number VARCHAR(20) OUTPUT
  AS
BEGIN
  DECLARE @number0_6 VARCHAR(7)
  DECLARE @number7_8 VARCHAR(2)
  DECLARE @number9_14 VARCHAR(6)
  DECLARE @number15_19 VARCHAR(5)
  SET @number0_6 = '622848'
  EXEC proc_cradTypeToVarchar @bank_crad_type, @number7_8 OUT
  SET @number9_14 = @bank_dot_number
  EXEC proc_countToVarchar @bank_dot_count, @number15_19 OUT
  SET @bank_crad_number = @number0_6 + @number7_8 + @number9_14 + @number15_19
END
SELECT @bank_crad_number
```

## 测试代码

```
-- 测试代码
DECLARE @a int
DECLARE @B VARCHAR(6)
DECLARE @C INT
DECLARE @num VARCHAR(20)
SET @a = 1
SET @B = '111111'
SET @C = 123

EXEC proc_createCradNumber @a, @B, @C, @num;
```



