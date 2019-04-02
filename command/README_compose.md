# linux pipeline
- netstat -nat|awk  '{print $6}'|sort|uniq -c|sort -rn  #查看当前连接，注意close_wait偏高的情况