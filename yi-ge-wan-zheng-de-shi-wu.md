一个事务的实例

```
-- 练习事务
DECLARE @number INT
DECLARE @temp INT
  SET @number = 1
  SET @temp = 1;
BEGIN TRANSACTION
  WHILE @number < 4
    BEGIN
      print @number
      set @number = @number + 1
      SET @temp = @temp + 1
    END;
  IF @number <> @temp
      BEGIN
        -- 出错
        -- 回滚
        print '交易失败，回滚事务.'
        rollback transaction
      END
    ELSE
      BEGIN
        commit transaction
        print @number
        print @temp

        print '交易成功，提交事务，写入硬盘，永久保存！'
      END
```



