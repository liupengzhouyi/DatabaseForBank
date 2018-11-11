# 名字表

## 数据表信息

| 字段名称 | 数据类型 | 是否主键 | 是否自增 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| name\_id | int | 是 | 是 | 名字编号 |
| name | varchar\(10\) | 否 | 否 | 名字 |

## 创建数据表的代码

```
-- 创建名字临时表
CREATE TABLE #temp_name_table
(
  -- 主键 ID
  name_id INT PRIMARY KEY IDENTITY (1, 1),
  -- 名字
  name VARCHAR(10) NOT NULL
);
```

## 插入数据

