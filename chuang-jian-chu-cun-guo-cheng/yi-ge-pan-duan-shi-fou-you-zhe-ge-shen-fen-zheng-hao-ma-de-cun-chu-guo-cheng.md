## 名称

```
proc_hasThisUserId
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @userId | VARCHAR\(20\) | 一个用户的身份证号码 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @returnValue | INT | 0或者1 |

## 代码

```
/**
创建一个判断又是存在某一个用户身份证号码存储过程
存储过程名称：proc_hasThisUserId
参数：
  @userId VARCHAR(20)
返回值：
  @returnValue INT
日期时间：2018年11月14日21点36分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_hasThisUserId
  @userId VARCHAR(20) ,
  @returnValue INT OUTPUT
  AS
BEGIN
  IF (SELECT user_ID FROM tb_user_table WHERE user_ID = @userId) IS NOT NULL
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
DECLARE @user_id VARCHAR(20)
DECLARE @returnValue INT
SET @user_id = '620621197207165383'
EXEC proc_hasThisUserId @user_id, @returnValue;
```



