# 一个取出姓氏的存储过程

## 名称

```
proc_randUserName
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @surName | VARCHAR\(20\) | 一个姓氏 |

## 代码

```
/**
创建一个存储过程
存储过程名称：proc_randSurName
参数：
  无。
返回值：
  1. @surName
日期时间：2018年11月14日21点11分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_randSurName
  @surName VARCHAR(20) OUTPUT
  AS
BEGIN
  SET @surName = (SELECT TOP 1 surname FROM tb_temp_surname_table ORDER BY NEWID())
END
SELECT @surName;
```

## 



