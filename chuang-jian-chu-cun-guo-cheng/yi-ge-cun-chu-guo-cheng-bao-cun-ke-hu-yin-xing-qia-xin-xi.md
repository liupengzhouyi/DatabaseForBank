# 一个存储过程保存客户银行卡信息

# 存储过程名称

```
proc_linkUserAndCrad
```

## 参数

| 参数名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| @user\_id | VARCHAR\(20\) | 身份证号码 |
| @crad\_number | VARCHAR\(20\) | 银行卡的卡号 |

## 返回值

| 返回值名称 | 数据类型 | 描述 |
| :--- | :--- | :--- |
| 无 | 无 | 无 |

## 代码

```
/**
创建一个存储过程保存客户银行卡信息
存储过程名称：proc_linkUserAndCrad
参数：
  @user_id VARCHAR(20)
  @crad_number VARCHAR(20)
返回值：
  无
日期时间：2018年11月15日14点11分
作者：刘鹏
版本：1.0.0
 */
CREATE PROCEDURE proc_linkUserAndCrad
  @user_id VARCHAR(20) ,
  @crad_number VARCHAR(20)
  AS
  BEGIN
    DECLARE @key_for_user INT
    DECLARE @key_for_crad INT
    DECLARE @number INT
    -- 判断是否有该用户
    EXEC proc_hasThisUserId @user_id, @key_for_user OUT
    -- 判断是否有该卡片
    EXEC proc_hasCradNumber @crad_number, @key_for_crad OUT
    IF @key_for_user = 1 AND @key_for_crad = 1
      BEGIN
        EXEC proc_howManyCrad @user_id, @number OUT
        INSERT INTO
          tb_user_bank_information_table(user_ID, bank_card_number, number)
        VALUES (@user_id, @crad_number, @number)
      END
    ELSE
      BEGIN
        PRINT '您的身份证号码或者您的银行卡号有问题'
      END
  END
```

## 测试代码

```
-- 测试代码
DECLARE @userId VARCHAR(20)
DECLARE @cradNumber VARCHAR(20)
SET @userId = ''
SET @cradNumber = ''
EXEC proc_linkUserAndCrad @user_id, @cradNumber;
```



