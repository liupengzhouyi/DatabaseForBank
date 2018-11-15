# 将数字转化为VARCHAR（2）的存储过程

# 存储过程名称

```
proc_cradTypeToVarchar
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @type | INT | 卡片类型 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @varcharType | VARCHAR\(2\) | varchar类型的数字 |

## 代码

```
/**
将数字转化为varchar类型的数据
存储过程名称：proc_cradTypeToVarchar
参数：
  @type INT
返回值：
  @varcharType VARCHAR(2)
日期时间：2018年11月14日15点07分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_cradTypeToVarchar
  @type INT ,
  @varcharType VARCHAR(2) OUTPUT
  AS
  BEGIN
    IF @type < 10
      BEGIN
        SET @varcharType = '0' + CAST(@type AS VARCHAR(1))
      END
    ELSE
      BEGIN
        SET @varcharType = CAST(@type AS VARCHAR(2))
      END
  END
  SELECT @varcharType
```

## 测试代码

```
-- 测试代码
DECLARE @type INT
SET @type = 1
DECLARE @varcharType VARCHAR(2)
EXEC proc_cradTypeToVarchar @type, @varcharType
```



