### CPU

查看 CPU 的型号
```
cat /proc/cpuinfo | grep 'model name' | sort | uniq
```

查看 CPU 个数
```
cat /proc/cpuinfo | grep 'physical id' | sort | uniq | wc -l
```

查看 CPU 核数
```
cat /proc/cpuinfo |grep "cores"|uniq|awk '{print $4}'
```

逻辑 CPU 核数
```
cat /proc/cpuinfo |grep "processor"|wc -l
```

