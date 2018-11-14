# 一个判断是否有这个电话号码的存在

## 名称

```
proc_hasThisPhoneNumber
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @phoneNumber | VARCHAR\(20\) | 一个电话号码 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @returnValue | INT | 0或者1 |

## 代码

```
/**
创建一个判断又是存在某一个用户电话号码存储过程
存储过程名称：proc_hasThisPhoneNumber
参数：
  @phoneNumber VARCHAR(20)
返回值：
  @returnValue INT
日期时间：2018年11月14日21点36分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_hasThisPhoneNumber
  @phoneNumber VARCHAR(20) ,
  @returnValue INT OUTPUT
  AS
BEGIN
  IF (SELECT user_phone_number FROM tb_user_table WHERE user_phone_number = @phoneNumber) IS NOT NULL
    BEGIN
      SET @returnValue = 1
    end
  ELSE
    BEGIN
      SET @returnValue = 0
    END
END
SELECT @returnValue;
```

## 测试代码

```
DECLARE @phoneNumber VARCHAR(20)
DECLARE @returnValue INT
SET @phoneNumber = '13856786586'
EXEC proc_hasThisPhoneNumber @phoneNumber, @returnValue;
```



