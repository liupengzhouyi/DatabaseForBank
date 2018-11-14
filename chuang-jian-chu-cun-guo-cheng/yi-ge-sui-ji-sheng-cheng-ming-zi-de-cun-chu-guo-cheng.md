# 一个随机生成名字的存储过程

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
| @name | VARCHAR\(20\) | 一个姓名 |

## 代码

```
/**
创建一个存储过程
存储过程名称：proc_randUserName
参数：
  无。
返回值：
  1. @name
日期时间：2018年11月14日21点26分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_randUserName
  @name VARCHAR(20) OUTPUT
  AS
BEGIN
  DECLARE @frist_name VARCHAR(10)
  EXEC proc_randSurName @frist_name OUT
  DECLARE @last_name VARCHAR(10)
  EXEC proc_randName @last_name OUT
  SET @name = @frist_name + @last_name
END
SELECT @name
```

### 测试代码

```
-- 测试数据代码
DECLARE @name VARCHAR(20)
EXEC proc_randUserName @name;
```



