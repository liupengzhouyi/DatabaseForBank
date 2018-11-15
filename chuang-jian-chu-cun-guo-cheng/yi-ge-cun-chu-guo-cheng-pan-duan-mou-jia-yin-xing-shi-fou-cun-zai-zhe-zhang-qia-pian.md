# 一个存储过程判断某家银行是否存在这张卡片

# 存储过程名称

```
proc_hasThisCrad
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @cradNumber | VARCHAR\(20\) | 卡号 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @returnValue | INT | 1或者0 |

## 代码

```
/**
创建一个存储过程判断某家银行是否存在这张卡片
存储过程名称：proc_hasThisCrad
参数：
  @cradNumber VARCHAR(20)
返回值：
  @returnValue INT
日期时间：2018年11月15日13点12分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_hasThisCrad
  @cradNumber VARCHAR(20) ,
  @returnValue INT OUTPUT
  AS
  BEGIN
    IF (SELECT * FROM tb_back_number_table WHERE bank_card_number = @cradNumber) IS NOT NULL
      BEGIN
        SET @returnValue = 1
      END
    ELSE
      BEGIN
        SET @returnValue = 0
      END
  END
  SELECT @returnValue;
```

## 测试代码

```

```



