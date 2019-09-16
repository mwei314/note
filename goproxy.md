针对vscode中对golang转到定义较慢的一些处理：
1. 升级到1.13
2. 设置proxy`go env -w GOPROXY=https://goproxy.cn,direct`，$$未测试$$Linux中使用export GOPROXY=https://goproxy.cn
> https://github.com/goproxy/goproxy.cn/blob/master/README.zh-CN.md#%E7%94%A8%E6%B3%95
3. 安装并设置gopls，打开VSCode的设置, 勾选go.useLanguageServe,默认情况下,Go扩展会提示你安装gopls。如果是网络的问题, 直接去https://github.com/golang/tools下载, 然后使用 go install github.com/golang/tools/cmd/gopls 安装
> 本人是先下载tools并解压到gopath相应位置，然后`go get github.com/golang/tools/cmd/gopls`，所以不清楚是proxy还是下载文件的效果