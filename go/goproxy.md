针对vscode中对golang转到定义较慢的一些处理：
1. 升级到1.13
2. 设置proxy`go env -w GOPROXY=https://goproxy.cn,direct`，$$未测试$$Linux中使用export GOPROXY=https://goproxy.cn
> https://github.com/goproxy/goproxy.cn/blob/master/README.zh-CN.md#%E7%94%A8%E6%B3%95
3. 安装并设置gopls，打开VSCode的设置, 勾选go.useLanguageServe,默认情况下,Go扩展会提示你安装gopls。如果是网络的问题, 直接去https://github.com/golang/tools下载, 然后使用 go install github.com/golang/tools/cmd/gopls 安装
> 本人是先下载tools并解压到gopath相应位置，然后`go get github.com/golang/tools/cmd/gopls`，所以不清楚是proxy还是下载文件的效果

## 190917补
个人pc按上面的方式还是不行，后来在GOPATH/src下创建golang.org/x文件夹，之后在其中git clone缺少的包，下载地址见`https://github.com/golang`

## 200114补
虚拟机go1.12版本下：  
```
export GO111MODULE=on
export GOPROXY=https://goproxy.io
```
后可以直接`go mod tidy && go mod vendor`，去掉go.mod中的replace部分也没有报错