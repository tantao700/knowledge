# 路径
## 绝对路径
    描述一个文件/文件夹的完整路径地址
    
    路径 = 绝对路径

|OS|例子|
|---|---|
|Linux/Mac|/ect/hosts|
|Windows|C:\Windows\System32\drivers\etc\hosts|

## 相对路径
    相对于当前文件夹来说去描述文件/文件夹的路径    
    路径 = 当前文件夹路径 + 当前路径 
    
|当前文件夹路径|当前路径|路径
|---|---|---|
| /home/user|./| /home/user/|
| /home/user|../| /home/|
| /home/user|.././| /home/|
| /home/user|../../| /|
| /home/user|documents| /home/user/documents/|
| /home/user|documents/../| /home/user/|
| /home/user|documents/files/| /home/user/documents/files/|

## 常用命令
|命令|说明|
|---|---|
|cd **-**|回退到上一次的文件夹|
|pwd|查看当前文件夹路径|
|~|用户根目录|
|cd ~|切换到 目录 **/Users/user/** 目录|
|clear|清屏|

## rm 删除

|命令|说明|
|---|---|
|~~sudo rm -rf  /~~|删除系统所有文件|
|pwd|查看当前文件夹路径|
|~|用户根目录|
|cd ~|切换到 目录 **/Users/user/** 目录|
|clear|清屏|