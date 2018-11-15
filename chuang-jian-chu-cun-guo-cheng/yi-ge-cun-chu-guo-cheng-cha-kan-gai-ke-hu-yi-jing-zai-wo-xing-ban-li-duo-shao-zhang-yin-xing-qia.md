# 一个存储过程查看该客户已经在我行办理多少张银行卡

# 存储过程名称

```
proc_howManyCrad
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @userId | VARCHAR\(20\) | 一个身份证号码 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @returnValue | INT | 一个数字，我有几张银行卡 |

## 代码

```
/**
创建一个存储过程查看该客户已经在我行办理多少张银行卡
存储过程名称：proc_howManyCrad
参数：
  @userId VARCHAR(20)
返回值：
  @number INT
日期时间：2018年11月15日12点37分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_howManyCrad
  @userId VARCHAR(20) ,
  @number INT OUTPUT
  AS
  BEGIN
    SET @number = (SELECT COUNT(*) 
                   FROM (SELECT * 
                          FROM tb_user_bank_information_table 
                          WHERE user_ID = @userId) temp_table)
  END
  SELECT @number
```

## 测试代码

```
-- 测试代码
DECLARE @userId VARCHAR(20)
DECLARE @number INT
SET @userId = ''
EXEC proc_howManyCrad @userId, @number
```



