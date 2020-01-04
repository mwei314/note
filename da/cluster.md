# 数据分析集群环境搭建

## 虚拟机安装Debian9

### 安装java
1. debian9默认使用openjdk，可以用`java -version`验证
2. 装Oraclejdk先卸载openjdk`sudo apt-get purge openjdk*`
3. 下载java1.8版本解压到/usr/local/java/jdk8
4. 配置环境变量，在/etc/profile中添加
```
export JAVA_HOME=/usr/local/java/jdk8
export CLASSPATH=.:$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar
export PATH=$PATH:$JAVA_HOME/bin
```
然后加载环境变量`source /etc/profile`
5. Debian下还需使用`update-alternatives`切换默认程序，先`update-alternatives --display java`查看java的信息，然后再
```
sudo update-alternatives --install /usr/bin/java java /usr/local/jdk1.8/bin/java [优先级]
sudo update-alternatives --install /usr/bin/javac javac /usr/local/jdk1.8/bin/javac [优先级]
```
最后用`sudo update-alternatives --config java`查看和进行检测
> 我这里优先级设置比原默认的高一些，还不清楚设置别的值有没有什么影响，需要再查一下update-alternatives的用法