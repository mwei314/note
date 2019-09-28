# 编译

## 交叉编译
Windows 下编译Linux 64位可执行程序
```
SET CGO_ENABLED=0
SET GOOS=linux
SET GOARCH=amd64
go build main.go
```

> vscode下的终端执行会有问题，原因待查