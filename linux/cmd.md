# 常用命令

## 查看文件个数
```
# 统计当前目录下文件的个数（不包括子目录）
ls -l | grep "^-" | wc -l

# 统计当前目录下文件的个数（包括子目录）
ls -lR| grep "^-" | wc -l

# 查看某目录下文件夹(目录)的个数（包括子目录）
ls -lR | grep "^d" | wc -l
```

## awk
```
awk '$10>100 {print $2}'
```