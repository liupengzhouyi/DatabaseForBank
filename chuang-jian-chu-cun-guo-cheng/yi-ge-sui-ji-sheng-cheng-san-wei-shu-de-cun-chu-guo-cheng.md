# 一个产生随机三位数的存储过程

## 名称

```
proc_hasCradNumber
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @returnValue | VARCHAR\(3\) | 一个三位的随机数 |

## 代码

```
/**
创建一个存储过程，产生一个随机的三位数，转型为VARCHAR(3)
存储过程名称：proc_createThreeNumber
参数：
  无
返回值：
  @returnValue VARCHAR(3)
日期时间：2018年11月14日23点46分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_createThreeNumber
  @returnValue VARCHAR(3) OUTPUT
  AS
  BEGIN
    SET @returnValue = CAST((RAND() * (888) + 110) AS INT)
  END
SELECT @returnValue
```

## 测试代码

```
--测试代码
DECLARE @number VARCHAR(3)
EXEC proc_createThreeNumber @number;
```



