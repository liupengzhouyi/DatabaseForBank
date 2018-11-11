# 姓氏表

## 数据表信息

| 字段名称 | 数据类型 | 是否主键 | 是否自增 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| surname\_id | int | 是 | 是 | 姓氏编号 |
| surname | varchar\(10\) | 否 | 否 | 姓氏 |

## 创建数据表的代码

```
--创建姓氏临时表
CREATE TABLE #temp_surname_table
(
  -- 主键 ID
  surname_id INT PRIMARY KEY IDENTITY (1, 1),
  -- 姓氏
  surname VARCHAR(10) NOT NULL
);
```

## 插入数据

