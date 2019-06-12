## this page introduce PG Database


```sql
-- 查看连接数变化
select count(1) from pg_stat_activity where state not like '%idle';

-- 追踪慢SQL
-- 1.0 install extension
create extension pg_stat_statements;
select pg_stat_reset();
select pg_stat_statements_reset();
-- 1.1 查询最耗时的SQL（一般就是导致问题的直接原因）
select * from pg_stat_statements order by total_time desc limit 5;

-- 1.2 查询读取Buffer次数最多的SQL，这些SQL可能由于所查询的数据没有索引，而导致了过多的Buffer读，也同时大量消耗了CPU
select * from pg_stat_statements order by shared_blks_hit+shared_blks_read desc limit 5;

-- 1.pg_stat_activity 查看一直不结束的SQL
select datname,
       usename,
       client_addr,
       application_name,
       state,
       backend_start,
       xact_start,
       xact_stay,
       query_start,
       query_stay,
       replace(query, chr(10), ' ') as query
from (
       select pgsa.datname                                   as datname,
              pgsa.usename                                   as usename,
              pgsa.client_addr                               as client_addr,
              pgsa.application_name                          as application_name,
              pgsa.state                                     as state,
              pgsa.backend_start                             as backend_start,
              pgsa.xact_start                                as xact_start,
              extract(epoch from (now() - pgsa.xact_start))  as xact_stay,
              pgsa.query_start                               as query_start,
              extract(epoch from (now() - pgsa.query_start)) as query_stay,
              pgsa.query                                     as query
       from pg_stat_activity as pgsa
       where pgsa.state != 'idle'
         and pgsa.state != 'idle in transaction'
         and pgsa.state != 'idle in transaction (aborted)'
     ) idleconnections
order by query_stay desc
limit 5;

-- 2.查看最耗时的SQL
select * from pg_stat_statements order by total_time desc limit 5;

-- 3.查看读取Buffer 次数最多的SQL
select * from pg_stat_statements order by shared_blks_hit+shared_blks_read desc limit 5;

-- 3.1 通过下面的查询，查出使用表扫描最多的表：
select * from pg_stat_user_tables where n_live_tup > 100000 and seq_scan > 0 order by seq_tup_read desc limit 10;
-- 3.2 查询当前正在运行的访问到上述表的慢查询：
select * from pg_stat_activity where query ilike '%<table name>%' and query_start - now() > interval '10 seconds';

-- 3.3 也可以通过pg_stat_statements插件定位涉及到这些表的查询：
select * from pg_stat_statements where query ilike '%<table>%'order by shared_blks_hit+shared_blks_read desc limit 3;

-- 4.0 处理慢查询 (杀死进程)
select pg_cancel_backend(pid) from pg_stat_activity where  query like '%<query text>%' and pid != pg_backend_pid();
select pg_terminate_backend(pid) from pg_stat_activity where  query like '%<query text>%' and pid != pg_backend_pid();


```