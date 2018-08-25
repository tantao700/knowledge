## nmap
 nmap –sT –sV –p80,443,8080 –P0 –n IP
    - sT scan with Tcp protocol
    - sV scan with Detail
    - p with port
# nmap -sP 192.168.1.0/24   
    - 仅列出指定网络上的每台主机，不发送任何报文到目标主机
# nmap -PS 192.168.1.234 
    - 探测目标主机开放的端口，可以指定一个以逗号分隔的端口列表(如-PS22，23，25，80)
# nmap -PU 192.168.1.0/24   
    - 使用UDP ping探测主机  
# nmap -sS 192.168.1.0/24     
    - 使用频率最高的扫描选项：SYN扫描,又称为半开放扫描，它不打开一个完全的TCP连接，执行得很快