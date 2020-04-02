# Common Command

## rm - *Remove files or directories*
|命令|描述|说明|
|---|---|---|
|rm /path/to/file /path/to/other/file|删除两个文件|-|
|rm -r /path/to/folder/|级联删除文件夹的文件|-|
|rm -rf /path/to/folder|级联删除文件夹的文件,f强制删除|-|
|rm -i files|交互删除多个文件,每次删除都弹出进行确认|-|
|rm -v /path/to/folder/*|删除文件并打印详细的记录|
|~~rm -rf /~~|删除根文件| <span style="color:red">*危险命令*</span>|


## ls - *List directory contents*
|命令|描述|说明|
|---|---|---|
|ls -l|列出所有文件|-|
|ls -a|列出所有文件|包含隐藏文件(.开头的文件 例如:**.bashrc**,**.vimrc**)|
|ls -la|列出所有文件|包含隐藏文件(.开头的文件 例如:**.bashrc**,**.vimrc**)|
|ls -ltr|格式化列出所有文件|通过修改时间排序|

## pwd - *Print name of current/working directory*
|命令|描述|说明|
|---|---|---|
|pwd|打印当前文件夹|-|
|pwd -P|解决所有软连接|显示物理路径|

## ssh - *Secure Shellis a protocol used to securely log onto remote systems*
|命令|描述|说明|
|---|---|---|
|ssh admin@xxx|使用用户名登录|-|
|ssh -i /path/to/key-file admin@xxx|使用private key|-|
|ssh admin@xxx -p 2222|使用端口:2222|-|
|ssh admin@xxx mkdir -p /path/to/folder|登录机器,然后执行 mkdir -p /path/to/folder|-|
|ssh -D 9999 -C admin@xxx|动态端口转发(SOCKS proxy on localhost:9999)|-|
|ssh -L 9999:xxx:80 -N -T admin@xxx|localhost:9999->xxx.com:80|-|
|ssh -J admin1@jump_xxx admin@xxx|通过jump_xxx 进行跳转|-|
|ssh -vT git@github.com|查看登录细节|-|

## scp - *Secure Copy*
|命令|描述|说明|
|---|---|---|
|scp /local/file admin@xxx:/remote/dir/|本地 -> 远程|-|
|scp admin@xxx:/remote/file /local/dir/| 远程-> 本地|-|
|scp -r admin@xxx:/remote/file /local/dir/| 远程-> 本地|-|
|scp -3 host1:/remote/file host2:/remote/dir/| 远程1--> 本地 --> 远程2|-|
|scp -i /local/private_key /local/file host0:/remote/dir/| 本地 --> 远程|使用私有key|

## nc - *Reads and writes tcp or udp data*
|命令|描述|说明|
|---|---|---|
|nc -l 8080 |监听一个8080端口|-|
|nc -l 127.0.0.1:8080 |监听一个8080端口|-|
|nc -w 200 127.0.0.1:8080 |设置一个超时时间|-|
|nc -l 8080\<file |服务一个文件|-|
|nc -zv 127.0.0.1 8080|tcp 查看端口是否可用|-|
|nc -zu 127.0.0.1 8080|udp 查看端口是否可用|-|


rsync -avzP --rsh=ssh file user@host:/home/user/path/to/file/

