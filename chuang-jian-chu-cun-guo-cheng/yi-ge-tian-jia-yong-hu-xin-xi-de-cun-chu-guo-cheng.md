## 名称

```
proc_saveUserDate
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @user\_id | VARCHAR\(20\) | 一个身份证号码 |
| @user\_name | VARCHAR\(20\) | 一个姓名 |
| @phoneNumber | VARCHAR\(15\) | 一个电话号码 |
| @address | VARCHAR\(45\) | 一个地址 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 代码

```
/**
创建一个存储数据存储过程
存储过程名称：proc_saveUserDate
参数：
  @user_id VARCHAR(20)
  @user_name VARCHAR(20)
  @phoneNumber VARCHAR(15)
  @address VARCHAR(45)
返回值：
  无
日期时间：2018年11月14日21点53分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_saveUserDate
  AS
BEGIN
  DECLARE @user_id VARCHAR(20)
  DECLARE @user_name VARCHAR(20)
  DECLARE @phoneNumber VARCHAR(15)
  DECLARE @address VARCHAR(45)
  EXEC proc_randUserName @user_name OUT
  EXEC proc_randIDNumberAndADAddress @user_id OUT, @address OUT
  EXEC proc_randPhoneNumber @phoneNumber OUT
  INSERT INTO tb_user_table(user_ID, user_name, user_phone_number, user_address)
  VALUES (@user_id, @user_name, @phoneNumber, @address)
END;
```

## 测试代码

```
EXEC proc_randIDNumber @id;
```



