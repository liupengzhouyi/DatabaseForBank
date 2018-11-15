# 创建一个储存过程产生身份证地区编号

## 名称

```
proc_randBankAddressNumber
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @bankAddressNumber | VARCHAR\(7\) | 银行卡的网点编号 |

## 代码

```
/**
创建一个存储过程，为了获取银行卡地区编号
存储过程名称：proc_randBankAddressNumber
参数：
  无
返回值：
  @bankAddressNumber
日期时间：2018年11月15日12点30分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_randBankAddressNumber
  @bankAddressNumber VARCHAR(7) OUTPUT
  AS
  BEGIN
    SET @bankAddressNumber = (SELECT TOP 1 dot_id FROM tb_dot_information_table ORDER BY NEWID())
  END
SELECT @bankAddressNumber;
```

## 测试代码

```
-- 测试代码
DECLARE @number VARCHAR(7)
EXEC proc_randBankAddressNumber @number;
```



