## 安装
使用rufus制作的启动U盘，选择使用dd镜像模式写入(**原因不清楚**)

## 源
选择国内源
`sudo pacman-mirrors -i -c China -m rank`
添加archlinuxchina源
`sudo vim /etc/pacman.conf`打开文件
在文件末尾添加以下两行
```
[archlinuxcn]
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```

## 安装迅雷
1. 安装yaourt`sudo pacman -S yaourt`
2. 修改AUR源`sudo vi /etc/yaourtrc`，将**AURURL**的注释去掉，改为国内源`AURURL=”https://aur.tuna.tsinghua.edu.cn”`
3. 安装迅雷`yaourt -S deepin.com.thunderspeed`(注：不要sudo)
> 安装过程很麻烦，最好不用

## 安装MySQL/Mariadb
arch默认不支持MySQL，但可以安装Mariadb，两者基本相同  
```
sudo systemctl stop mysqld //停止mysql服务，可以不用
sudo pacman -S mariadb libmariadbclient mariadb-clients //安装mariadb
sudo mysql_install_db --user=mysql --basedir=/usr --datadir=/var/lib/mysql

sudo systemctl start mariadb //启动项目
sudo mysql_secure_installation //设置root密码、初始化等操作，必须sudo，否则可能没权限执行
sudo systemctl restart mariadb //重启
```
之后就可以使用`mysql -u root -p`连接数据库了。

## Redis
下载地址：https://redis.io/
```
# 解压
tar xzvf redis...
# 进入解压后的路径
cd redis...
# 编译
sudo make
# 进入编译路径
cd src/
# 测试安装
sudo make test
# 安装
mkdir /usr/local/redis
sudo make install PREFIX /usr/local/redis
# 启动
cd /usr/local/redis/bin
cp redis.../redis.conf ./
./redis-server redis.conf
```
> 这种启动方式似乎没法关闭，最好开启redis.conf中的daemon，让redis后台运行，还有开机自启动待处理

## MySQL
自2013年起，MariaDB就被Arch Linux当作官方默认的MySQL实现。Oracle MySQL已被移动到AUR，本地测试的话没有特别要用Oracle MySQL的理由，就直接使用mariadb，不折腾了。  
```
# 安装
sudo pacman -S mariadb
# 初始化
sudo mysql_install_db --user=mysql --basedir=/usr --datadir=/var/lib/mysql
# 启动并设置开机自启动
sudo systemctl start mariadb
sudo systemctl enable mariadb
# 设置密码，初始密码是空
sudo mysql_secure_installation
```

然后`mysql -u root -p`测试连接，也可以使用可视化工具workbench，安装命令`sudo pacman -S mysql-workbench`

### MySQL新建用户和授权
```
CREATE USER '{用户名}'@'{host}' IDENTIFIED BY '{密码}';
GRANT {privileges} ON {dadabasename}.{tablename} TO '{用户名}'@'{host}';
```
说明：
- host：本地用localhost，从任意远程主机登陆用通配符%
- privileges：用户的操作权限，如SELECT，INSERT，UPDATE等，如果要授予所的权限则使用ALL
- dadabasename.tablename：数据库名和表名，所有使用通配符* 
> 用以上命令授权的用户不能给其它用户授权，如果想让该用户可以授权，用`GRANT privileges ON databasename.tablename TO 'username'@'host' WITH GRANT OPTION;`

## 无法提交处理 (无效或已损坏的软件包)
```
# 更新密钥，要先安装archlinux-keyring
sudo pacman-key --refresh-keys

# 重新加载签名密钥
sudo pacman-key --init
sudo pacman-key --populate

# 清除pacman的缓冲文件
sudo pacman -Scc

# 更新
sudo pacman -Syu
```


## 安装MongoDB
```
git clone https://aur.archlinux.org/mongodb-bin.git
cd mongodb-bin
makepkg -si
# 启动
systemctl start mongodb
# 开机启动
systemctl enable mongodb
# 测试连接
mongo
```
>  https://stackoverflow.com/questions/59455725/install-mongodb-on-manjaro