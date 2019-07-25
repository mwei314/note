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
