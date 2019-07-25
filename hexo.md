# 应用
详情见[官方文档](https://hexo.io/zh-cn/docs/)

* 安装`npm install -g hexo-cli`
* 建站
    ```
    hexo init <folder>
    cd <folder>
    npm install
    ```
* 新建文章`hexo new [layout] <title>`
* 生成静态文件`hexo generate`
* 启动服务器`hexo server`
* 部署`hexo deploy`
* 清除缓存文件 (db.json) 和已生成的静态文件 (public)`hexo clean`

# 保存源码
* git上新建仓库blogsource
* clone到本地
* add source/* _config.yml
* commit