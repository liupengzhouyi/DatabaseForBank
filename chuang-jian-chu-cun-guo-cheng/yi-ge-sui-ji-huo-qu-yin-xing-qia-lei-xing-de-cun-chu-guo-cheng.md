# 一个随机获取银行卡种类编号的存储过程

## 名称

```
proc_randBackCradTpeyNumber

```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @backCradTypeNumber | INT | 银行卡种类编号 |

## 代码

```
/**
创建一个存储过程，为了获取银行卡的类型
存储过程名称：proc_randBackCradTpeyNumber
参数：
  无
返回值：
  @bankCradTypeNumber
日期时间：2018年11月14日23点53分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_randBackCradTpeyNumber
  @bankCradTypeNumber INT OUTPUT
  AS
  BEGIN
    SET @bankCradTypeNumber = (SELECT TOP 1 bank_card_types_number FROM tb_list_of_bank_card_type ORDER BY NEWID())
  END
SELECT @bankCradTypeNumber;
```

## 测试代码

```
-- 调用储存过程
DECLARE @number INT
EXEC proc_randBackCradTpeyNumber @number;
```



