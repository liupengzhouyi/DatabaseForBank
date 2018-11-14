# 这就是一个坑，埋葬了我的至少5个小时

## 我非常的后悔，我为什么如此的优秀，但是没有办法， 最后通过和丁雨老师的一起努力找Bug，我们终于找到了原因所在，我非常佩服丁雨老师的耐心，可能我现在已经被这个辐照的这回影响了，做事情都在急功近利，就像照顾一样，就喜欢玩短线。没有耐心去找到Bug，但是丁雨老师太有耐心了，我自己都要放弃了，不去搞存储过程的嵌套，放弃代码的复用性，但是依旧换案例，找到Bug原因。最后锁定Bug，嵌套过程返回数据，这是一个好大的坑，我不知道说一些什么比较好呢？总算是解决了这个问题。

## 我的测试代码如下

### 查看存储过程的嵌套是否在运行
```
CREATE PROCEDURE prc_t101
  as
BEGIN
  SELECT '123456'
  print '123456'
end;

exec prc_t101;

create procedure prc_t1_201
  as
BEGIN
  exec prc_t101
  SELECT '1122334477'
  print '1122556'
end;

EXEC prc_t1_201;
```

### 我们确定了储存过程的嵌套的过程是可以执行的
### 只是我无法吧值带出来
### 那么问题来了：如何为把值带出被嵌套的储存过程
### 这是设我们的答案


```
CREATE PROCEDURE proc_randNumber01
  @number INT OUTPUT
  AS
BEGIN
  SET @number = RAND() * 100
  print @number
END
SELECT @number;

DECLARE @num INT
EXEC proc_randNumber01 @num

CREATE PROCEDURE proc_numberAddNumber03
  @number0 INT OUTPUT
  AS
BEGIN
  DECLARE @numberI INT
  DECLARE @numberII INT
  EXEC proc_randNumber01 @numberI OUT
  print @numberI
  EXEC proc_randNumber01 @numberII OUT
  PRINT @numberII
  SET @number0 = @numberI + @numberII
END
SELECT @number0;

DECLARE @num INT
EXEC proc_numberAddNumber03 @num
```

### 这个储存过程是为了计算俩个随机数的和
谢谢！

再次感谢丁雨老师

