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