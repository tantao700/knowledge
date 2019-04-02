# 基础命令
- awk '{print $4,$6}' f.txt
- awk '{print NR,$0}' f.txt cpf.txt
- awk '{print FNR,$0}' f.txt cpf.txt
- awk '{print FNR,FILENAME,$0}' f.txt cpf.txt
- awk '{print FILENAME,"NR="NR,"FNR="FNR,"$"NF"="$NF}' f.txt cpf.txt
- echo 1:2:3:4 | awk -F: '{print $1,$2,$3,$4}

# 内建变量
NR:NR表示从awk开始执行后，按照记录分隔符读取的数据次数，默认的记录分隔符为换行符，因此默认的就是读取的数据行数，NR可以理解为Number of Record的缩写。

FNR:在awk处理多个输入文件的时候，在处理完第一个文件后，NR并不会从1开始，而是继续累加，因此就出现了FNR，每当处理一个新文件的时候，FNR就从1开始计数，FNR可以理解为File Number of Record。

NF: NF表示目前的记录被分割的字段的数目，NF可以理解为Number of Field