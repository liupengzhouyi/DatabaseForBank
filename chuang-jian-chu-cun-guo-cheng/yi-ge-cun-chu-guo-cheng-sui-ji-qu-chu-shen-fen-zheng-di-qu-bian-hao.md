# 一个存储过程随机取出身份证地区编号

## 名称

```
proc_randUserIdAddressNumber
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @userIdAddressNumber | VARCHAR\(7\) | 身份证的地区编号 |

## 代码

```
/**
创建一个存储过程随机取出身份证地区编号
存储过程名称：proc_randUserIdAddressNumber
参数：
  无
返回值：
  @userIdAddressNumber
日期时间：2018年11月15日12点37分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_randUserIdAddressNumber
  @userIdAddressNumber VARCHAR(7) OUTPUT
  AS
  BEGIN
    SET @userIdAddressNumber = (SELECT TOP 1 address_number FROM tb_temp_address_table ORDER BY NEWID())
  END
SELECT @userIdAddressNumber;
```

## 测试代码

```
-- 测试代码
DECLARE @number VARCHAR(7)
EXEC proc_randUserIdAddressNumber @number;
```



