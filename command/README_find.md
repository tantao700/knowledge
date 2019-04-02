# find
- find . -name 'keyword'
- sudo -u admin find /home/admin /tmp /usr -name \*.log(多个目录去找)
- find . -iname \*.txt(大小写都匹配)
- find . -type d(当前目录下的所有子目录)
- find /usr -type l(当前目录下所有的符号链接)
- find /usr -type l -name "z*" -ls(符号链接的详细信息 eg:inode,目录)
- find /home/admin -size +250000k(超过250000k的文件，当然+改成-就是小于了)
- find /home/admin f -perm 777 -exec ls -l {} \; (按照权限查询文件)
- find /home/admin -atime -1  1天内访问过的文件
- find /home/admin -ctime -1  1天内状态改变过的文件
- find /home/admin -mtime -1  1天内修改过的文件
- find /home/admin -amin -1  1分钟内访问过的文件
- find /home/admin -cmin -1  1分钟内状态改变过的文件
- find /home/admin -mmin -1  1分钟内修改过的文件

# find & grep
- find . -name '*.log' -exec grep -Hi 'import' {} \; # 查找文本为import的文件