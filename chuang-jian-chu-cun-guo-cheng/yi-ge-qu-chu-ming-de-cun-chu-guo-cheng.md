# 一个随机取出的名

## 名称

```
proc_randName
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @name | VARCHAR\(20\) | 一个名 |

## 代码

```
/**
创建一个存储过程
存储过程名称：proc_randName
参数：
  无。
返回值：
  1. @name
日期时间：2018年11月14日21点15分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_randName
  @name VARCHAR(20) OUTPUT
  AS
BEGIN
  SET @name = (SELECT TOP 1 name FROM tb_temp_name_table ORDER BY NEWID())
END
SELECT @name;
```



