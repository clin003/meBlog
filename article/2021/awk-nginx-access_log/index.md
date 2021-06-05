# awk 分析 nginx 运行日志常用指令



awk 分析 nginx 运行日志常用指令


1.独立IP
```bash
awk '{print $1}' access.log | sort -r |uniq -c | wc -l
```

2.统计PV
```bash
awk '{print $6}' access.log | wc -l
```

3.查询访问最频繁的URL
```bash
awk '{print $7}' access.log|sort | uniq -c |sort -n -k 1 -r|more
```

4.查询访问最频繁的IP
```bash
awk '{print $1}' access.log|sort | uniq -c |sort -n -k 1 -r|more
```

5.UV统计：
```bash
awk '{print $6}' access.log | sort -r |uniq -c |wc -l
```

6.按小时统计
```bash
cat access.log |awk '{print $4}' | awk -F ':' '{print $1,$2}'|uniq -c | awk '{print $2" "$3" "$1}'
```
