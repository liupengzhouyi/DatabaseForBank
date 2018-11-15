# 一个存储过程获取当前地区的某种卡片已经产生了多少张

## 存储过程名称

```
proc_getCardCountInDot
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @addressNumber | VARCHAR\(7\) | 网点编号 |
| @type | INT | 卡片种类 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @count | INT | 一个数字记录卡片数量 |

## 代码

```
/**
创建一个存储过程获取当前地区的某种卡片已经产生了多少张
存储过程名称：proc_getCardCountInDot
参数：
  @addressNumber VARCHAR(7)
  @type INT
返回值：
  @count INT
日期时间：2018年11月15日14点33分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_getCardCountInDot
  @addressNumber VARCHAR(7) ,
  @type INT ,
  @count INT OUTPUT
  AS
BEGIN
  SET @count = (SELECT dot_count FROM tb_temp_dot_table WHERE dot_number = @addressNumber AND card_type = @type)
END
SELECT @count;
```

## 测试代码

```
-- 调用储存过程
DECLARE @addressNumber VARCHAR(7)
DECLARE @type INT
DECLARE @count INT
SET @addressNumber = '152529'
SET @type = 5
EXEC proc_getCardCountInDot @addressNumber, @type, @count;
```



