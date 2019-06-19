# Explain

|执行计划运算类型 | 操作说明 | 启动时间 | 
| ---- | ------- | ------------- |
|Seq Scan|扫描表(全表扫描)|无|
|Index Scan|索引扫描|无|
|Bitmap Index Scan|索引扫描|有|
|Bitmap Heap Scan|索引扫描|有|
|Subquery Scan|子查询|无|
|Tid Scan|ctid = …条件|无|
|Function Scan|函数扫描|无|
|Nested Loop|循环结合|无|
|Merge Join|合并结合|有|
|Hash Join|哈希结合|有|
|Sort|排序，ORDER BY操作|有|
|Hash|哈希运算|有|
|Result|函数扫描，和具体的表无关|无|
|Unique|DISTINCT，UNION操作|有|
|Limit|LIMIT，OFFSET操作|有|
|Aggregate|count, sum,avg, stddev集约函数|有|
|Group|GROUP BY分组操作|有|
|Append|UNION操作|无|
|Materialize|子查询|有|
|SetOp|INTERCECT，EXCEPT|有|


# 分析常用关键字
|执行计划运算类型 | 操作说明 |
| ------- | ------- | 
| explain {SQL} | 执行计划(不真正执行) |
| explain analyze {SQL}| 执行计划(真正执行),并评估时间|
| analyze {TABLE}| 分析TABLE 数据信息|
| cost=0.43..8.45| 0.43:执行到返回第一行时需要的cost & 8.45:执行整个SQL的cost|