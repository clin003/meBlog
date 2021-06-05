# Linux 常用命令


Linux 常用命令

### 日期
```bash
$(date -d '1 day ago' '+%Y-%m-%d')
```
常用方法
### 数字格式化
```bash
part=`printf "%03d" $i` # 左补0
```
### 删除旧文件
```bash
# 找出5天前修改的文件名以.tar结尾的文件进行删除
find /www/backup -mtime +5 -name "*.tar"  |xargs rm
```

### for循环
```bash
for ((i=0;i<10;i++))
do
_date=$(date +%Y-%m-%d -d "${i} day")
echo $_date
done
#
for i in {1..10}
do
        echo $i
done
```

### 文件合并
```bash
find ./ -name "item*" | xargs sed 'a\' > all.txt
find ./ -name "item*" | xargs cat > all.txt
:s/old/new           #替换当前行的第一个old为new
:s/old/new/g         #替换当前行的所有的old为new
:.,$s/old/new        #替换当前行到最后行的第一个old为new
:.,$s/old/new/g      #替换当前行到最后行的所有old为new
:N,Ms/old/new        #替换第N行到第M行的第一个old为new
:N,Ms/old/new/g      #替换第N行到第M行的所有old为new
:N,Ms/old/new/gc     #替换第N行到第M行的所有old为new，且逐一询问是否删除
:%s/old/new          #替换所有行的第一个old为new
:%s/old/new/g        #替换所有行的所有old为new
```

### 文件排序、交集、并集、差集
```bash
#排序
sort a.txt |uniq -c
#一、交集
sort a.txt b.txt | uniq -d
#二、并集
sort a.txt b.txt | uniq
#三、差集 a.txt-b.txt:
sort a.txt b.txt b.txt | uniq -u
#差集 b.txt - a.txt:
sort b.txt a.txt a.txt | uniq -u
```

### 删除重复行
```bash
sort -k2n all.txt | uniq > real.out
sort -k2n all.txt | awk '{if ($0!=line) print;line=$0}'
sort -k2n all.txt | sed '$!N; /^\(.*\)\n\1$/!P; D'
```

### 删除空格
```bash
cat all.txt |sed s/[[:space:]]//g
```
### awk 去重
```bash
awk '!($1 in a){a[$1];print $1}'
#或
sort $1 | uniq 
# awk结果使用逗号间隔拼接
awk -F ',' '{print $1}' | xargs | tr ' ' ','
```

### 常用状态查看
```bash
# 按CPU和内存倒序前n个进程
ps -aux --sort -pcpu,+pmem | head -n 5
# 按进程名查看
ps -f -C java
```


### 文件同步rsync
```bash
rsync -zvrtopgl --progress --delete /fromDist/ root@s1:/toDist/
```

### 链接状态统计
```bash
netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'
# TCP连接状态详解 
# LISTEN: 服务器在侦听来自远方的TCP端口的连接请求
# SYN-SENT: 在发送连接请求后等待匹配的连接请求
# SYN_RECV: 一个连接请求已经到达，等待确认
# SYN-RECEIVED: 再收到和发送一个连接请求后等待对方对连接请求的确认
# ESTABLISHED: 代表一个打开的连接/正常数据传输状态/当前并发连接数
# FIN_WAIT1: 等待远程TCP连接中断请求，或先前的连接中断请求的确认/应用说它已经完成
# FIN_WAIT2: 从远程TCP等待连接中断请求/另一边已同意释放
# CLOSE-WAIT: 等待从本地用户发来的连接中断请求
# CLOSING: 等待远程TCP对连接中断的确认/两边同时尝试关闭
# LAST-ACK: 等待原来的发向远程TCP的连接中断请求的确认/等待所有分组死掉
# TIME-WAIT: 等待足够的时间以确保远程TCP接收到连接中断请求的确认/另一边已初始化一个释放
# ITMED_WAIT:  等待所有分组死掉
# CLOSED： 没有任何连接状态
```

### CPU/内存/系统信息查看
```bash
# cpu
grep "model name" /proc/cpuinfo 
cat /proc/cpuinfo | grep name | cut -f2 -d: | uniq -c
cat /proc/cpuinfo | grep physical | uniq -c
# cpu位数
echo $HOSTTYPE
# 内存
grep MemTotal /proc/meminfo 
# linux 版本
cat /etc/redhat-release
cat /etc/os-release
cat /etc/lsb-release
# linux 内核版本
uname -a 
uname -r
```


### 常用监控工具
```bash
# 网络监控
iftop
# IO监控
iotop
# 负载监控
htop
top
```


### 进程监控
```bash
pidstat -p 843 1 3 -u -t
# -u：代表对 CPU 使用率的监控
# 参数 1 3 代表每秒采样一次，一共三次
# -t：将监控级别细化到线程
```


### ssh相关
```bash
# 秘钥生成
ssh-keygen -t rsa -b 4096 -C "your_hostname"
# 免密登录
cat ~/.ssh/id_rsa.pub | ssh  root@ip "cat >> .ssh/authorized_keys"
```

### firewalld防火墙使用
```bash
# 禁止ping
firewall-cmd --permanent --add-rich-rule='rule protocol value=icmp drop'
# 允许192.168.1.0/24主机所有连接
firewall-cmd --add-rich-rule='rule family="ipv4" source address="192.168.1.0" accept'
# 禁止某IP访问
firewall-cmd --permanent --zone=public --add-rich-rule="rule family=ipv4 source address='123.56.247.76/24' reject"
# 开放端口
firewall-cmd --zone=public --permanent --add-port=8080/tcp
firewall-cmd --reload
```


### 文件统计
```bash
ls -g |awk 'BEGIN{sum=0}{sum+=$4}END{print sum/(1024*1024*1024)}'
```


### history格式及数量修改
```bash
export HISTSIZE=10000
export HISTTIMEFORMAT=" %Y-%m-%d %H:%M:%S - `who am i 2>/dev/null | awk '{print $NF}'|sed -e 's/[()]//g'` - `who -u am i |awk '{print $1}'` "
export PROMPT_COMMAND="history 1 >> /var/log/.myhistory" #将命令记录输出到文本中
touch /var/log/.myhistory
chmod  /var/log/.myhistory
```
