# 一个存储过程随机获取一个用户

# 存储过程名称

```
proc_getRandUser
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @user\_id | VARCHAR\(20\) | 一个用户的身份证号码 |

## 代码

```
/**
创建一个存储过程随机获取一个用户
存储过程名称：proc_getRandUser
参数：
  无
返回值：
  @user_id VARCHAR(20)
日期时间：2018年11月15日16点53分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_getRandUser
  @user_id VARCHAR(20) OUTPUT
  AS
  BEGIN
    SET @user_id = (SELECT TOP 1 user_ID FROM tb_user_table ORDER BY NEWID())
  END
  SELECT @user_id;
```

## 测试代码

```
-- 测试代码
DECLARE @user_id VARCHAR(20)
EXEC proc_getRandUser @user_id;
```



